---
title: "Golang Fanin - Fanout  Reading 10k files in seconds"
date: "2021-01-27"
---

Sometimes you've got some tasks which consume a lot of time to be processed, for instance, the invoice generation for a big company, NLP tasks, or any file processing tasks you could imagine.

Golang has a powerful feature known by all, based on goroutines (concurrency) and channels (messaging) that define totally the Fanin - Fanout pattern.

The main idea is to paralelize jobs based on I/O and CPU execution doing the next tasks, but using the concurrency to launch severals goroutines to paralize the execution flow:

* **Read file** -> Actually, using concurrency we'll read 10k files in few seconds launching goroutines

* **Channels** -> Using Channels we'll create the pdf after reading the file and get the buffer data into the channel

* **Controller** -> Using bool channel we'll control the whole process to finish the execution (into main function)

Let's go with the example:

First of all, we'll create the structs which will support the information as well as generic functions just to read a file and then write a pdf in golang:
```golang
const (
  path = "/tmp/files"
)

type (
  StreamData struct {
    data     []byte
    fileName string
  }
)

func loadFileNames() string {
  info, err := ioutil.ReadDir(path)
  if err != nil {
    panic(err)
  }

  var fileNames []string
  for _, i := range info {
    fileNames = append( fileNames, path + "/" + i.Name() )
  }
  return fileNames
}

func generatePdf(data []byte, fileName string) {   
  pdfFile := gofpdf.New("P", "mm", "A4", "arial")   
  pdfFile.AddPage()   
  pdfFile.SetFont("arial", "", 12)   
  pdfFile.Cell(40,10, string(data))   
  if err := pdfFile.OutputFileAndClose( fileName + ".pdf" ); err != nil{
      fmt.Println(err)   
  } 
}
```

Now, with the basic structure created, we're going to create the first read file function using goroutines and channels:

```golang
func openFiles(paths []string) <-chan StreamData {
  streamOut := make(chan StreamData)     //create the channel type Data with the information once has been loaded
  go func() {                           // goroutine to read from dir
    for _, p := range paths {
      f, err := os.Open(p)
      if err != nil {
        fmt.Println(err)
      }
      b, _ := ioutil.ReadAll(f)
      streamData := StreamData{data: b, fileName: f.Name()}
      streamOut <- streamData      //send data to the channel
    }
    close(streamOut)
  }()
  return streamOut.                 //return the channel info
}
```

The idea is to share information between concurrent routines using channels to do that. That's the sense of the pattern name -> Fanin - fanout

As you can, imagine we have to implement the second part of the solution. We are going to create just a function to build a pdf file getting the information from the channel as return the function openFile:

```golang

func convertToPdf(done chan bool, streamIn <-chan StreamData) <-chan StreamData {
  streamOut := make(chan StreamData)
  go func() {                       
    for stream := range streamIn {
      generatePdf(stream.data, stream.fileName)
    }
    close(streamOut)
    done <- true
  }()
  return streamOut
}

```


Using the same structure we're launching the goroutine to generate the pdf, using the information for the IN channel to generate the OUT information in the channel.

Just to finish our main function creates a bool channel to know when the file processing has been finished. This is another important thing to keep in mind, because goroutines are running in background so that's one of the controls that you have to control the execution.

```golang
func main() {
  start := time.Now()
  files := loadFileNames()

  done := make(chan bool)

  inputStream := openFiles(files)
  convertToPdf(done, inputStream)
  <-done

  fmt.Printf("\nTime finished in %f\n", time.Since(start).Seconds())
}

```
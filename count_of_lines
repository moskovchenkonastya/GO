package main

import (
    "bufio"
    "fmt"
    "io"
    "log"
    "os"
    //"path/filepath"
    //"strings"
)

func main() {


    inFilename, err := filenameFromCommandLine()
    if err != nil {
        fmt.Println(err)
        os.Exit(1)
    }

    inFile := os.Stdin

    if inFilename != "" {
        if inFile, err = os.Open(inFilename); err != nil {
            log.Fatal(err)
        }
        defer inFile.Close()
    }

    count := CountOfLines(inFile)
    fmt.Println(count)

}

func filenameFromCommandLine() (inFilename string, err error) {


    if len(os.Args) > 1 {
        inFilename = os.Args[1]
    }   

    if inFilename == "" {
        log.Fatal("won't overwrite the infile")
    }

    return inFilename, nil
}

func CountOfLines(inFile io.Reader) (int) {
    var err error
    reader := bufio.NewReader(inFile)
    i := 0
    eof := false
    for ;!eof ; i++{
        var line string
        line, err = reader.ReadString('\n')
        fmt.Println(line)
        if err != nil {
            if err == io.EOF {
                break
            }
        log.Fatal("failed to finish reading the file: ", err)
        }
    }

    return i
}



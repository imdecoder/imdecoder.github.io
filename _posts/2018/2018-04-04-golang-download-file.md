---
layout: single
title: "Download a file from url in Golang"
date: 2018-04-04 15:16:52 +1000
guid: urn:uuid:22aa69ba-0375-4ff4-8488-f0e1a864e363
tags:
  - dev
  - golang
categories:
  - dev
external-url: 
feature: false
---

[1]: https://golangcode.com/download-a-file-from-a-url/

Example to download a file from url and save on local

`io.Copy()` read 32kb (maximum) from input and write to output reapeatly, so dont need worry about memory.

    func DownloadFile(filepath string, url string) error {
        // Create the file
        out, err := os.Create(filepath)
        if err != nil {
            return err
        }
        defer out.Close()

        // Get the data
        resp, err := http.Get(url)
        if err != nil {
            return err
        }
        defer resp.Body.Close()

        // Write the body to file
        _, err = io.Copy(out, resp.Body)
        if err != nil {
            return err
        }

        return nil
    }

reference: [Code Example][1]
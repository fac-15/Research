# Streams and Buffers
![gif](https://media.giphy.com/media/l0HlIMvkBCH23wyUU/giphy.gif)

### Research what streams and buffers are in Node, how are they used in conjunction?

Streams and buffers are purely Node concepts.
Node is a runtime environment.
**Data ==(Streams)=> Buffers ==(Streams)=> Client**



## <Streams>
![](https://i.imgur.com/iAXAXPA.png)
- A sequence of data being moved from one point to the other over time
- Stream in Node.js simply means a sequence of data being moved from one point to the other over time. 
- The whole concept is, you have a huge amount of data to process, but you don’t need to wait for all the data to be available before you start processing it.
- Streams can read/write data chunk by chunk, without buffering the whole file at once.
- Streams provide a way to read or write data in chunks, rather than all at once. 
- Stream is just a **process of flow of data** from the data source to the buffer and from the buffer to the client.All these bits flow in a stream.

#### Stream Benefits:
* Abstraction for continuous chunking of data.
* No need to wait for the entire resource to load.
* Ability to handle **enormous** data files!

#### Stream is Used In:
* HTTP request & responses
* Standard input/output(stdin & stdout)
* File reads and write

#### Type of Stream:
* Readable Stream
* Writable Stream
* Duplex Stream
* Transfer Stream

#### What is Piping in a Stream?
Piping is a process in which we provide the output of one stream as the input to another stream. It is normally used to get data from one stream and to pass the output of that stream to another stream. There is no limit on piping operations.

## <Buffers>

![](https://i.imgur.com/hE7lV5a.png)
The official **Node.js docs** states in part…
>
>"…  a mechanism for reading or manipulating streams of binary data. The Buffer class was introduced as part of the Node.js API to make it possible to interact with octet streams in the context of things like TCP streams and file system operations."
>
 - Node.js provides Buffer class which provides instances to store raw data.
 - **“waiting area”** is the buffer! It is **a small physical location** in your computer, usually in the RAM, where data are temporally gathered, wait, and are eventually sent out for processing during streaming.

- Manipulate or interact with streams of binary data
- Buffers provide **lower-level access** to data in memory than the V8 engine provides itself. 
- These small chunks can be used **simultaneously**, without waiting for the whole amount of the data to download.
- A buffer is raw set of data with **no defined type**. This means that anything can be a buffer:
   - text file
   - image
   - video
   - an array...

- If the rate the data arrives is faster than the rate the process consumes the data, the excess data need to wait somewhere for its turn to be processed.
- e.g. Watching a youtube video without downloading the whole file.
- e.g. Rather than reading an entire 100 MB text file into memory and processing it all at once, you can "stream" the data in smaller, **more manageable portions**. 

## The Whole Process:

We can think of the whole stream and buffer process as a bus station. 
![](https://i.gifer.com/origin/fc/fc1c308e9e8d79fb859b75a08ac3eced_w200.gif)
In some bus stations, a bus is not allowed to depart until a certain amount of passengers arrive or until a specific departure time. 
Passengers who arrive earlier will need to wait until the bus station decides to send the bus on its way. 
While passengers who arrive when the bus is already loading or when the bus has already departed need to wait for the next bus.
![](https://78.media.tumblr.com/72420c51c67e93f956df370ea6373839/tumblr_moreiprr471s0o9k1o1_500.gif)



### Create a Node project that lets a user run the command node bigtextfile.txt in the same directory as bigtextfile.txt and stream the contents of the file to the users terminal. Need a big file? How about a book.





### (Bonus) Allow an additional argument to be provided in the command to specify a time interval of how often a chunk of text from the file is streamed to the terminal. E.G node bigtextfile.txt 1s


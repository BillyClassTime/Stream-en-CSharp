# Utilizando Stream en Csharp

**Usando BinaryReader y Binary Writer**

**Usando StreamReader y Stream Writer**

## Making Binary Writer

```csharp
public void MakingBinaryWriter()
{
    string destinationFilePath = @".\fourthcoffee\applicationdata\settings.txt";
    // Collection of bytes.
    byte[] dataCollection = { 1, 4, 6, 7, 12, 33, 26, 98, 82, 101 };
    // Create a FileStream object so that you can interact with the file
    // system.
    FileStream destFile = new FileStream(
        destinationFilePath, // Pass in the destination path.
        FileMode.Create, // Always create new file.
        FileAccess.Write); // Only perform writing.
    // Create a BinaryWriter object passing in the FileStream object.
    BinaryWriter writer = new BinaryWriter(destFile);
    // Write each byte to stream.
    foreach (byte data in dataCollection)
    {
        writer.Write(data);
    }
    // Close both streams to flush the data to the file.
    writer.Close();
    destFile.Close();
    Console.ReadLine();
}
```

## Making Binary Reader

```csharp
public void MakingBinaryReader()
{
    // Source file path.
    string sourceFilePath = @".\fourthcoffee\applicationdata\settings.txt ";
    // Create a FileStream object so that you can interact with the file
    // system.
    FileStream sourceFile = new FileStream(
     sourceFilePath, // Pass in the source file path.
     FileMode.Open, // Open an existing file.
     FileAccess.Read);// Read an existing file.
                      // Create a BinaryWriter object passing in the FileStream object.
    BinaryReader reader = new BinaryReader(sourceFile);
        int position = 0;
    // Store the length of the stream.
    int length = (int)reader.BaseStream.Length;
    // Create an array to store each byte from the file.
    byte[] dataCollection = new byte[length];
    int returnedByte;
    while ((returnedByte = reader.Read()) != -1)
    {
        // Set the value at the next index.
        dataCollection[position] = (byte)returnedByte;
        Write($"{returnedByte},");
        // Advance our position variable.
        position += sizeof(byte);
    }
    // Close the streams to release any file handles.
    reader.Close();
    sourceFile.Close();
    Console.ReadLine();
}
```

## Making Stream Writer

```csharp
public void MakingStreamWriter()
{
    string destinationFilePath = @".\fourthcoffee\applicationdata\settingsStreams.txt ";
    string data = "Hello, this will be written in plain text";
    // Create a FileStream object so that you can interact with the file
    // system.
    FileStream destFile = new FileStream(
    destinationFilePath, // Pass in the destination path.
    FileMode.Create, // Always create new file.
    FileAccess.Write); // Only perform writing.
    // Create a new StreamWriter object.
    StreamWriter writer = new StreamWriter(destFile);
    // Write the string to the file.
    writer.WriteLine(data);
    // Always close the underlying streams to flush the data to the file
    // and release any file handles.
    writer.Close();
    destFile.Close();
    Console.ReadLine();
}

```

## Making Stream Reader

```csharp
public void MakingStreamReader()
{
    string sourceFilePath = @".\fourthcoffee\applicationdata\settingsStreams.txt ";
    // Create a FileStream object so that you can interact with the file
    // system.
    FileStream sourceFile = new FileStream(
     sourceFilePath, // Pass in the source file path.
     FileMode.Open, // Open an existing file.
     FileAccess.Read);// Read an existing file.
    StreamReader reader = new StreamReader(sourceFile);
    StringBuilder fileContents = new StringBuilder();
    // Check to see if the end of the file
    // has been reached.
    while (reader.Peek() != -1)
    {
        // Read the next character.
        fileContents.Append((char)reader.Read());
    }
    // Store the file contents in a new string variable.
    string data = fileContents.ToString();
    WriteLine(data);
    // Always close the underlying streams release any file handles.
    reader.Close();
    sourceFile.Close();
    Console.ReadLine();
}

```




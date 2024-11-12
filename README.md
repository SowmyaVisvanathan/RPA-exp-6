### Name : Sowmya V
### Reg no : 212222110045
### Date : 
# Exercise 6 - Copy and Rename Files

### Aim:
To copy all files from a source folder to a destination folder and rename them by appending a timestamp to the file names.

### Software required:
UiPath Studio-community edition


### Procedure:

1. **Initialize Variables**:
   - **Define Source and Destination Paths**:
     - Use an **Assign** activity to set the `source` variable with the path of the source folder. 
     - Use another **Assign** activity to set the `destination` variable with the path of the destination folder.
      
2. **Retrieve Files from Source Folder**:
   - Use an **Assign** activity to retrieve the list of files from the source directory and store it in the `files` variable. 
   - Make sure `files` is defined as `List<String>` or `String[]`.

3. **Loop Through Each File**:
   - Add a **For Each** activity to iterate through each file in the `files` list.
   - Set **TypeArgument** in the **For Each** activity to `String` to ensure it processes each file path as a string.

4. **Extract File Details**:
   - Inside the loop, use the following **Assign** activities to process each file:
     - **filename**: Extract the name of the file without its path:
       ```vb
       filename = Path.GetFileName(item)
       ```
     - **file_ext**: Extract the file extension:
       ```vb
       file_ext = Path.GetExtension(item)
       ```
     - **timestamp**: Generate a timestamp for unique file identification:
       ```vb
       timestamp = Now.ToString("yyyyMMddHHmmss")
       ```

5. **Create New File Name with Timestamp**:
   - Use an **Assign** activity to construct the new file name with the timestamp appended:
     ```vb
     newfilename = filename + "_" + timestamp + file_ext
     ```

6. **Copy and Rename the File to Destination Folder**:
   - Add a **Copy File** activity to copy the file from the source to the destination folder with the new filename.
   - Configure the properties as follows:
     - **From**: Set this to `item`, which holds the path of the current file being processed in the loop.
     - **To**: Set this to `Path.Combine(destination, newfilename)`, which constructs the path in the destination folder with the new file name.
     - **Overwrite**: Enable this option to allow overwriting if a file with the same name exists.

7. **Run the Workflow**:
   - Execute the workflow. It will:
     - Copy each file from the source folder to the destination folder.
     - Rename each file with a unique timestamp to prevent overwriting.


### Main.xaml:

![Screenshot 2024-11-12 102946](https://github.com/user-attachments/assets/69740809-7520-476c-8bbc-45b15fbd57eb)

![image](https://github.com/user-attachments/assets/939c3b54-3979-4ff1-9152-a05988e89559)



### Output:

### 1. Source Folder
![Screenshot 2024-11-10 191925](https://github.com/user-attachments/assets/e1b07235-fb13-47c0-9b52-ff93918a8ffd)

### 2. Destination Folder
![Screenshot 2024-11-10 191909](https://github.com/user-attachments/assets/eae5b3be-cf2d-4c65-8c0e-c9bd0db86e0a)


### Results:
Thus, the files from the source folder were successfully copied and renamed with a timestamp in the destination folder. 



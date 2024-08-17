# Distributed File System (Using Socket Programming)

## Project Overview

This project implements a distributed file system using socket programming. The system is composed of three servers—Smain, Spdf, and Stext—and multiple clients. The Smain server acts as the main server that handles all client requests, while Spdf and Stext servers are responsible for handling `.pdf` and `.txt` files, respectively.

### Key Features:

- **Multi-Client Support:** The system supports multiple clients simultaneously, each communicating only with the Smain server.
- **File Distribution:** Clients upload `.c`, `.pdf`, and `.txt` files to Smain. The Smain server stores `.c` files locally and forwards `.pdf` and `.txt` files to the Spdf and Stext servers, respectively, without the client's awareness.
- **Command Processing:** Clients can upload, download, delete files, create tar archives, and display file lists using custom commands.

## Project Structure

The project consists of the following main components:

1. **Smain.c:** Handles client connections and manages file distribution between the main server and auxiliary servers.
2. **Spdf.c:** Dedicated server for storing and managing `.pdf` files.
3. **Stext.c:** Dedicated server for storing and managing `.txt` files.
4. **client24s.c:** Client-side program that interacts with the Smain server to perform various file operations.

## Commands

The client can use the following commands to interact with the distributed file system:

### 1. `ufile filename destination_path`

- **Description:** Uploads a file from the client's working directory to the specified path on the Smain server.
- **Parameters:**
  - `filename`: Name of the file to upload (`.c`, `.pdf`, `.txt`).
  - `destination_path`: Destination path on Smain (`~/smain`).
- **Example:**
  ```bash
  ufile sample.c ~/smain/folder1/folder2
  ```

### 2. `dfile filename`

- **Description:** Downloads a file from the Smain server to the client's working directory.
- **Parameters:**
  - `filename`: Name of the file to upload (`.c`, `.pdf`, `.txt`).
- **Example:**
  ```bash
  dfile ~/smain/folder1/folder2/sample.pdf
  ```

### 3. `rmfile filename`

- **Description:** Deletes a file from the Smain server.
- **Parameters:**
  - `filename`: Path of the file to delete (`.c`, `.pdf`, `.txt`).
- **Example:**
  ```bash
  rmfile ~/smain/folder1/folder2/sample.txt
  ```

### 4. `dtar filetype`

- **Description:** Creates a tar archive of all files of the specified type and downloads the tar file to the client's working directory.
- **Parameters:**
  - `filetype`: File type to archive (`.c`, `.pdf`, `.txt`).
- **Example:**
  ```bash
  dtar .pdf
  ```

### 5. `display pathname`

- **Description:** Displays a list of all .c, .pdf, and .txt files in the specified directory on the Smain server.
- **Parameters:**
  - `pathname`: Path of the directory on Smain (`~/smain`).
- **Example:**
  ```bash
  display ~smain/folder1/folder2
  ```

## Setup and Execution

### Prerequisites

- **Linux-based operating system**
- **GCC compiler**

### Steps to Run

#### 1. Compile the server and client programs:

```bash
gcc -o smain Smain.c
gcc -o spdf Spdf.c
gcc -o stext Stext.c
gcc -o client client24s.c
```

#### 2. Run the servers on separate terminals:

```bash
./smain
./spdf
./stext
```

#### 3. Run the client:

```bash
./client
```

## Project Submission

### This project is submitted as part of the COMP-8567 course for the Summer 2024 session. It involves demonstrating the project during a scheduled slot and undergoing a viva.

## Authors

- **Vrutik Parmar**

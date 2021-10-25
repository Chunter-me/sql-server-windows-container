# SQL Server Windows Docker Image w/Full-Text
Windows SQL Server image based on Microsoft base image but includes SQL Server Full-Text Indexing.

I use this image to run my Aptify Databases for development purposes from.


**NOTES**
- The following is all based on having **Docker Desktop** installed locally on a local windows 10 or 11 machine.

- This is a Windows Container, make sure to have your Docker Desktop switch to Widnows Containers.

- Run commands from either Windows Terminal, PowerShell or the Command Prompt.

## Build Local Docker Image
You can build your own local image:<br>
`docker build -t <ORG/COMPANY/PERSONAL ACRONYM>/<IMAGE NAME> <FOLDER PATH TO DOCKERFILE>`

Example if your terminal is within the root of this repo:<br>
`docker build -t chunterme/sql-windows .\Dockerfile`

## OR: Pull from my personal Docker Hub
You can pull the image from docker hub:<br>
`docker pull chunterme/sql-windows:latest`

## Create Container
`docker run -d -p <DesiredPort>:1433 --env sa_password=<SA PASSWORD> --mount type=bind,source=<LOCAL PATH>\,destination=C:\Data\ --name <IMAGE NAME> chunterme/sql-windows:latest`

## DB/Backup Files
Move either you backup file or DB file to the `<LOCAL PATH>` you specified in the create container command. These file will now be accessable for you to attach or restore from when you connect to the sql instance.

## Connect to SQL Instance
Open SSMS or Azure DataStudio or what ever your prefered editor is.

Your server is `127.0.0.1,<DesiredPort>`

Where the `<DesiredPort>` is the port number you entered in the create container command.

Restore or Attach your DB and your on your way.


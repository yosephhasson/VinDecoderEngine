# VinDecoderEngine

A lightweight C# console application that reads VINs from a SQL Server table, decodes them using the NHTSA Vehicle API, and extracts trim-level data using manufacturer-specific parsing rules.

## Overview

This project was built to automate VIN decoding for vehicles stored in a database. The application:

- Connects to SQL Server and reads VIN values from a table
- Calls the NHTSA VIN decode API for each VIN
- Parses the API response
- Extracts trim information based on manufacturer-specific logic
- Writes the parsed VIN and trim output to the console

The solution is currently organized as a simple console app with separate folders for API requests, database access, parsing logic, and response models. It targets **.NET Framework 4.6.1** and uses **Newtonsoft.Json** for JSON deserialization. :contentReference[oaicite:1]{index=1}

## How It Works

1. The app opens a database connection and selects VIN values from:

   `DeveloperDB.dbo.Vehicle_VIN`

2. For each VIN, it sends a request to the NHTSA VIN decode endpoint.

3. The API response is deserialized into strongly typed classes.

4. The parser inspects the decoded variables and determines which field should be used as the trim, depending on the manufacturer.

5. The parsed VIN and trim are printed to the console. :contentReference[oaicite:2]{index=2}

## Project Structure

```text
GetVinData
├── GetVinData.sln
└── GetVinData
    ├── API
    │   └── Requests.cs
    ├── DB_Connection
    │   └── DB_Connection.cs
    ├── Data
    │   └── Data.cs
    ├── Parsers
    │   └── Parser.cs
    ├── App.config
    ├── GetVinData.csproj
    └── Program.cs

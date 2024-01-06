# town-treasurer-tools
Tools for common town treasury data parsing that run entirely in the user's web browser. No data leaves the user's computer.

## Usage
- This tool is a webpage designed for someone, likely my wife or someone who works with her, to drag an OpenGov Munis import file onto it.
- The page parses the file and creates links for downloading the data in the format my wife needs.
- None of the data from the Munis file is uploaded anywhere. All parsing and new file creation happen in the browser. Essentially, it's using the browser as a local application to do all the work, ensuring the data remains private to the computer accessing this page.

## Data Privacy and Security 

- No uploads to external servers: All data processing occurs within your browser, ensuring that your sensitive information never leaves your computer.
- Runs on your computer: The tool runs in your web browser as a local application, meaning everything happens on your side, keeping your data secure with the same level of privacy and secuirty as if you were using Excel on your computer.
- This tool is hosted at https://pauljeffrussell.github.io/town-treasurer-tools/. By using the online version, you automatically receive enhancements.
- I will never make changes that send data off your computer, but this requires that you trust me. If you would like complete control over updates, you can load these files onto your own web server. Doing so ensures that no changes to these files are made without you reviewing and installing them yourself.

## Why does this exist
The OpenGov Munis import file has a bonkers format. I mean it's a CSV, but it looks like this:

```
H,0,04222022,P Russell,,5555,E-23-758,MS,,3
D,B110,210,Electrical,,,,,,0
H,0,04232023,Q Smith,,,FMKT-23-64,MS,,4
D,H110,75,Farmer's M,,,,,,0
```

The issue is that these files often combine multiple rows for different types of payments on different dates, which is odd given that they need to be imported separately. Even stranger, when you try to import this information into Munis, Munis expects:

1. Only one type of transaction per import file. Transactions are defined by the last number in a row.
2. All transactions of a given type grouped by date in separate files.
3. The row following a transaction row needs to remain with it. So transaction data is really split into two separate rows with different column values. Seriously, who came up with this format?!


So, this tool parses a provided Munis file and breaks it into import files in the way my wife told me she needed them. If any developers for Munis are available for a beer, I'd love to understand how this format came to be.

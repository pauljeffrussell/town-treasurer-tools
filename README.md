# town-treasurer-tools
Tools for common town treasury data parsing that run completely in the users web browser. No data leaves the users computer.

## Usage
- This tool is a webpage expects someone, probably my wife or someone that works with her, to drag an OpenGov Munis import file onto it. 
- The page parses the file and creates links where you can download the data in the format my wife needs it in. 
- None of the from the Munis file is uploaded anywhere. All the parsing and new file creation happens in the browser. So essentially it's using the browser as a local application to do all the work and the data remains private to the computer accessing this page. 

## Why does this exist
The OpenGov Munis import file has a bonkers format. I mean it's CSV, but it looks like this:

H,0,04222022,P Russell,,5555,E-23-758,MS,,3
D,B110,210,Electrical,,,,,,0
H,0,04232023,Q Smith,,,FMKT-23-64,MS,,4
D,H110,75,Farmer's M,,,,,,0

The issue is that these files often combine a bunch of rows for different types of payments on different dates. Which is just weird. What is even stranger is that when you try to import this information into Munis, Munis expects:
1. Only one type of transaction per import file. Transatctions are defined by the last number in a row.
2. All transactions of a give type grouped by date in separate files. 
3. The row following a transaction row to stay with it, because who doesn't break transaction data into 2 separate rows with different column values. I ask you. Seriously. Who came up with this format!!!

So this tool parses out a provided Munis file and breaks it into import files the way my wife told me she needed them. If any of the developers for Munis are free for a beer, I'd love to know how this format happened. 



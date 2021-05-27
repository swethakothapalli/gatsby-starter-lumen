---
title: "Moving files from one location to other using python"
date: "2021-05-27T19:27:32.169Z"
template: "post"
draft: false
slug: "moving-files-from-one-location-to-other"
category: "Python"
tags:
- "python"
description: "how to move the files which is of anytype from one location to other."
socialImage: "static/media/files_copying.png"
---

**Move files from one location to other using python** Do you know there is a simple library in python where you can move file from one place to other in a matter of seconds. if you don't let me introduce the library to you that is **shutil**

let me tell you how we will use this library in python for moving files

![Files moving](static/media/files_copying.png)

## single file moving from one location to other

+ For doing this you no need not  install any pre-packages.
+ you can directly import it.

```python
import shutil
original = (r'the path of the original file')
target = (r'the path of the target location')
shutil.move(original,target)
```

Now you have moved the file from one location to other so easily with just a single command. 

<figure>
	<blockquote>
		<p>Now what if you have to pick hundred's of files among thousands of files to move from one location to other . it will be quite tidious task to do it manually right. don't worry i will show you how to do it with in seconds programatically with this **shutil** library</p>
		<footer>
		</footer>
	</blockquote>
</figure>

### multiple files moving from one location to other

+For doing this you need to import shutil .
+ Also you to import xlrd (importing xlrd supposing your file names were there in an excel sheet).

Now let's see how we will move mutlple required files among lots of files in a folder

```python
import shutil
import xlrd

loc = (r"C:\Users\python\Desktop\test\file_list.xlsx") #Location for masterlist of tickers
wb = xlrd.open_workbook(loc) #opening the workbook
sheet = wb.sheet_by_index(0) #navigating to the sheet by giving its index number
 
for i in range(1,sheet.nrows): #omiting first row as mostly it will contain info about header
    
    try:    
        file_name = (sheet.cell_value(i, 1))# assuming the filenames were there in column 1 
        original = (r'C:\Users\pyhton\Desktop\rough\original_folder\{}.xlsx'.format(file_name))#original folder location
       
        target = (r'C:\Users\pyhton\Desktop\rough\target_folder\{}.xlsx'.format(file_name))#target folder location

        shutil.move(original,target)#moving the files from original to targer folder
            
    except:
        print(file_name) # if there is no file in the orignal folder which is in your excel sheet that will be printed here
```

That's it you have simply mutliple files from one location to other very easily in no time. try it and save your time!!!!!



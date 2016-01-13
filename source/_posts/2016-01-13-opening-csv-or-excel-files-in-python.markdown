---
layout: post
title: "Opening CSV or Excel files in Python"
date: 2014-12-17 00:03:46 -0600
comments: true
categories: 
---

A recent project of mine has involved being very flexible with input data, transforming it to a standardized format, and putting it into a database. This is commonly referred to as <a href="http://en.wikipedia.org/wiki/Extract,_transform,_load">ETL</a>, or Extract, Transform, Load.

In doing this project, I've gotten familiar with an awesome Python Data Analysis framework called <a href="http://pandas.pydata.org/">Pandas</a>. To install Pandas, simply pull one of these in the ol' command line:

    sudo pip install pandas

Now you're ready to use the pandas library! The basic functionality takes some kind of data input, whether it be CSV, JSON, Excel, or a number of different formats, and converts it into a DataFrame object.

This DataFrame object is great because it can be indexed and you can perform all kinds of operations on the data. For my purposes, I only wanted to get all the data into this standardized format, then get it out in dictionary-like objects for each row. I was only concerned with using Excel and CSV files (as this post title indicates), so here's the function I used:

    def open_file(filepath):
        if ".csv" in filename: 
            doc =  pd.read_csv(filepath)
        if ".xls" in filename: 
            doc = pd.read_excel(filepath, 0, index_col=None, na_values=['NA'])

        return [dict([(colname, row[i]) for i,colname in enumerate(doc.columns)]) for row in doc.values]

You may be thinking "what could that possibly do!?!" Well, it does quite a few things! If you give it a file path that contains .csv or .xls (which includes .xlsx), it'll open it and put it in a DataFrame. Then it takes the DataFrame and constructs a list of dictionaries, each one containing the headers from the first line of the file and the values from each successive row.

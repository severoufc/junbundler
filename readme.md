# JUnbundler

JUnbundler is a tool aimed to support the unbundling process of Java projects and it's part of a exploratory study on API unbunding. Software unbundling consists of the division of a software into bundles (smaller and/or specialized modules) usually due to emerging features that deserves to become a product on their own, maintenance easiness, team wotk division, etc. The exploratory study supported by JUnbundler focus on API undundability based on client usage, which analyses how the API clients usage migth be take in account throught the unbundling process of those APIs.

# Steps to reproduce the unbudling process

To run the unbundling process, import the JUnbundler project into your workspace and execute the JUnbundler class (jubundler/src/main/java/JUnbundler.java). This dataset comes with our APIs list configured into "jubundler/apis/apis.json" but you are free to include and exclude to APIs you want to analyze.

This project consumes a list of API clients which are mined with the [BOA](http://boa.cs.iastate.edu/) language and infrastructure.

Basic workflow is described bellow: (If you do not want to perform the analysis for a API of your choice, skip to step 8)

1. Choose your target API for analysis;
2. Go to "junbundler/apis" folder and create a directory for your own API as follows:
---- junbundler/
-------- apis/
------------ {API_NAME}/
---------------- data/
-------------------- input/
-------------------- output/
----------------- scripts/
----------------- source/

3. Download your API source and copy it into data/source inside your API folder. Compacted files should be extracted;
4. Collect the API base package (i.e., for Google Gson API the base package is 'com.google.gson');
5. Copy the template script for API clients mining is available on "jubundler/scripts/boa-imports-template.boa" and change the target package name with yours;
6. Go to the BOA website (see Related Links), request a user account. Log in, go to the "Run Examples" page and submit the code from step 4;
6.1 Your job will be executed on the BOA infrastructure for a while. Once it is finished, download the output file (if there is any) on the "Job List" page;
6.2 Copy the BOA output file into your API data/input folder with the following name: imports_[API_NAME].txt (e.g., for Gson it would be imports_Gson.txt);
7. Edit the "junbundler/apis/apis.json" file including an entry for your API. A detailed description of each key of this file can be found in the "Source" folder of this dataset.
8. Run the JUnbundler class ("junbundler/src/main/java/JUnbundler.java").

# About execution and results:

- This program execution includes large text files parsing, Trinagular Dependency Matrix construction and API source code structure analysis, thus it can take a while to complete, from several minutes up to few days, depending on your machine specifications and target APIs for analysis. Be aware that APIs which yields huge usage files may take a lot of memory to build Trinagular Dependency Matrix. It's recommended to have at least 8GB of RAM to run this program with the current API set.
- All result files will be located in the "studies" folder under the project root directory with the name "unbundling-study-{EXECUTION_TIMESTAMP}", where {EXECUTION_TIMESTAMP} correspond to the time the program finished.

# Troubleshooting

If you have any issues while running the JUnbundler program or need assistance, please contact us.


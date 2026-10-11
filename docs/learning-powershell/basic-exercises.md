# Basic PowerShell Exercises

These exercises are designed for people who have just finished the [PowerShell Beginner's Guide](powershell-beginners-guide.md).
Work through them in order in a PowerShell session. Each exercise builds on the previous one, and a sample answer is provided at the end of each section so you can check your work.

We recommend creating a scratch folder for these exercises so that you do not affect other files on your computer:

```powershell
PS /> New-Item -ItemType Directory -Path ./ps-exercises
PS /> Set-Location ./ps-exercises
```

## Exercise 1: Create and Inspect a File

Create a file named `notes.txt` that contains the text `My first PowerShell file`, then display its contents.

Sample answer:

```powershell
PS /> Set-Content -Path ./notes.txt -Value "My first PowerShell file"
PS /> Get-Content -Path ./notes.txt
My first PowerShell file
```

## Exercise 2: Add Content to an Existing File

Add a second line `I am learning PowerShell` to `notes.txt` without removing the first line, then display the file.

Sample answer:

```powershell
PS /> Add-Content -Path ./notes.txt -Value "I am learning PowerShell"
PS /> Get-Content -Path ./notes.txt
My first PowerShell file
I am learning PowerShell
```

## Exercise 3: Create Several Folders

Create three folders named `reports`, `logs`, and `archive` inside the `ps-exercises` folder.

Sample answer:

```powershell
PS /> New-Item -ItemType Directory -Path ./reports, ./logs, ./archive
```

## Exercise 4: List Only the Files

List all items in the `ps-exercises` folder, but show only the files and not the folders.

Sample answer:

```powershell
PS /> Get-ChildItem -Path . -File
```

Hint: use `Get-Help Get-ChildItem -Parameter File` to read about the `-File` switch.

## Exercise 5: Copy and Rename a File

Copy `notes.txt` to the `archive` folder as `notes-backup.txt`.

Sample answer:

```powershell
PS /> Copy-Item -Path ./notes.txt -Destination ./archive/notes-backup.txt
PS /> Get-ChildItem -Path ./archive
```

## Exercise 6: Filter Items by Name

Create files `report1.txt`, `report2.txt`, and `log1.txt` in the `ps-exercises` folder. Then list only the files whose name starts with `report`.

Sample answer:

```powershell
PS /> "" > report1.txt
PS /> "" > report2.txt
PS /> "" > log1.txt
PS /> Get-ChildItem -Path . -Filter report*
```

## Exercise 7: Search Text in a File

Use `Select-String` to find every line in `notes.txt` that contains the word `PowerShell`.

Sample answer:

```powershell
PS /> Select-String -Path ./notes.txt -Pattern "PowerShell"
```

## Exercise 8: Count the Lines in a File

Count how many lines are in `notes.txt`.

Sample answer:

```powershell
PS /> (Get-Content -Path ./notes.txt).Count
2
```

## Exercise 9: Sort Items by Size

Using the pipeline, list the files in the `ps-exercises` folder sorted by size, largest first.

Sample answer:

```powershell
PS /> Get-ChildItem -Path . -File | Sort-Object -Property Length -Descending
```

## Exercise 10: Clean Up

Delete the `archive` folder and everything in it, then confirm that it no longer exists.

Sample answer:

```powershell
PS /> Remove-Item -Path ./archive -Recurse
PS /> Test-Path -Path ./archive
False
```

## Challenge: Combine What You Have Learned

Write a short script named `summary.ps1` that:

1. Lists all `.txt` files in the current folder.
1. Displays the number of lines in each file.

Save the script with a `.ps1` extension and run it with `./summary.ps1`. See [Create and Run PowerShell Scripts](create-powershell-scripts.md) for help.

Sample answer:

```powershell
Get-ChildItem -Path . -Filter *.txt -File | ForEach-Object {
    $lineCount = (Get-Content -Path $_.FullName).Count
    "{0}: {1} lines" -f $_.Name, $lineCount
}
```

## Next Steps

- Read [Working with PowerShell Objects](working-with-powershell-objects.md) to learn more about the objects that cmdlets return.
- Use `Get-Help` on any command you do not recognize.

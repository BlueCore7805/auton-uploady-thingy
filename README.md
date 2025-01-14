# Auton Uploady Thingy
A seamless script to enhance your PROS VEX Robotics projects by automating the process of updating and uploading autonomous codes.  
**[Note]** This is still in alpha. Bugs are to be expected. Contributions are welcome!

---

## Getting Started

1. **Download the Script**  
   Visit the [Releases Page](#) and download the appropriate script for your operating system:
   - **Linux**: `pros.sh`
   - **Windows**: `pros.ps1`

2. **Place the Script in Your Project Folder**  
   Copy the downloaded script file into your PROS project directory.

---

## Configuration

Before using the script, you'll need to configure a few settings to match your project's requirements:

### For Both Linux and Windows
1. **Update File Paths**  
   Open the script and modify the following lines to match your project structure:
   ```ps1
   variablesFile="./path/to/file" #Example ./src/variable.cpp
   projectFile="./project.pros"
   
2. **Set the Auton Selector Line**\
    Configure the line that the script uses to identify the auton selector in your variables.cpp.\
    Example Configurations:
    ```ps1
    autonSelectorLine="int auton =" 
    autonSelectorLine="std::string auton ="
    
3. **Declare Autons**\
    Define your auton slots and their associated names in the ``projectNames`` section:\
    [Note] Whatever you put in ``name`` is what gets changes in project.pros\
    Autons will be ordered\uploaded in order under ```projectNames``` unless declared otherwise
    
    Example Configurations:
    ```sh
    #Linux/macOS
    declare -A projectNames=(
        [1]="Red Left"
        [blue]="Blue Right"
    )
    
    declare -A customSlots=(
        [blue]=3 #Auton blue will be uploaded to slot 3
    )

    #Windows
    $projectNames = @{
        1 = @{ Name = "Red Left"; CustomSlot = $null }; #When set to $null means no custom slot
        "blue" = @{ Name = "Blue Right"; CustomSlot = 3 };
    }
    
4. **Auton Groups**\
    Grouping your autons in sections to upload automatically with one command!\
    Example Configurations:
    ```sh
    #Linux/macOS
    #Do not put commas between different autons. You can repeat autons but idk why you would.
    declare -A autonKeywords=(
        [group]="1 test" 
    )
    
    #Windows
    $autonKeywords = @{
        "group" = @(1, "test"); #Pretty obvious
    }l
    
## Usage
Now your finished configuring your list. You can always go back and add/remove to your needs.

I will be using the example configuration used above as a example.
### Linux/macOS
    ./pros.sh blue

- Changes your auton value to "blue"
- Changes your project name to "Blue Right"
- Uploads project to 3rd slot

### Windows
    .\pros.ps1 1

- Changes your auton value to 1
- Changes your project name to "Red Left"
- Uploads project to 1st slot

## Important Notes
* When you are using text as your auton selector without a custom slot. It will default to where that auton is on the list. Shown below: ``Red`` will be on the ``first slot`` while ``blue`` will be on the ``second slot``.
    ```sh
    declare -A projectNames=(
        [red]="Red Left" 
        [blue]="Blue Right"
    )

* When using auton groups, slots that are not filled/listed in the configueration will be turned into empty slots when uploading.
* Make sure you set up everything correctly before running your script. If not, it might cause unexpected changes to your code. Luckily, no major changes will affect your code if something as gone wrong.
* I am not responsible for any damage that might cause by using this script.
 
## Join my discord
Have suggestions? Bugs? Join the [discord](https://discord.gg/EMgbwcZMFs) to help contribute to this project:D \
Dicord is not finished yet so everything is kinda bad...


## Thanks too 
- [BestUsernamEver](https://github.com/BestUsernamEver) - Suggesting the name
- [Me, myself and I](https://github.com/BlueCore7805) - Making this whole project, duh

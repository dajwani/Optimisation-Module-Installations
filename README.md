# Optimisation-Module-Installations

# Getting Started
You will use Jupyter Notebook, Julia (v1.11.2), and Xpress throughout the course. Please follow the installation guidance below **sequentially**. Note that the screenshots in this instruction set are from an earlier version of Julia.

## Install Anaconda and Jupyter Notebook
- If you already have Jupyter Notebook installed, go ahead and install Julia (jump right into the next step)
- If you don’t have Jupyter Notebook on your local machine, [install Anaconda](https://www.anaconda.com/products/individual-d)

## Install Julia
1. [Download Julia V1.11.2](https://julialang.org/downloads/) and install: follow the installation instructions
2. Open Julia Command-Line: type in 'Julia' in the search bar and click on 'Julia 1.11.2'
3. In Julia Command-Line, type the following commands one after another

    - Type in ``using Pkg`` and then press Enter
![type using Pkg in Julia Command-Line](https://github.com/dajwani/Optimisation-Module-Installations/blob/main/static/Install_Julia_package1.PNG)

    - Then type in ``Pkg.add("IJulia")``, press Enter, and wait for the package to be added
![type using Pkg in Julia Command-Line](https://github.com/dajwani/Optimisation-Module-Installations/blob/main/static/Install_Julia_package2.PNG)

4. Now let's create your first Julia notebook!
    - Run jupyter notebook. (If you are not familiar with Jupyter Notebook, follow the short instruction [here](https://pythonforundergradengineers.com/opening-a-jupyter-notebook-on-windows.html)) 
    - Click on the “New” button at the top right of your local jupyter notebook server, then choose "Julia 1.11.2"
    ![create new Julia notebook](https://github.com/dajwani/Optimisation-Module-Installations/blob/main/static/Create_new_Julia_notebook.png)

    - Once a new jupyter notebook is set up, you should see Julia’s icon on the *top right* of the new notebook  
    ![check Julia's icon in newly-created notebook](https://github.com/dajwani/Optimisation-Module-Installations/blob/main/static/Create_new_Julia_notebook2.png)

[Reference](https://www.geeksforgeeks.org/add-julia-kernel-to-jupyter/)


## Install the FICO Xpress MP
1. Go to the [Xpress Community License application website](https://content.fico.com/xpress-optimization-community-license) and fill in your information to apply for a community license
2. Once submit, you'll be directed to a download page. Choose the **Xpress (Workbench, Mosel & Solver)** installation package that suits your operation system

![Xpress Download options](https://github.com/dajwani/Optimisation-Module-Installations/blob/main/static/Install_Xpress.PNG)

3. Run the installation file once downloaded. Choose 'continue to install' or 'trust' or 'open' this app on receipt of security warning
4. Installation begins
    - *For Windows/Mac*
      
      - Click on 'setup' if prompted (see instructions [here](https://www.fico.com/fico-xpress-optimization/docs/latest/installguide/dhtml/chapinst1_sec_secwin.html))
      
      - Follow the instructions, choose the 'Community License' when asked
      
      - When you see the 'Choose Destination Location' page, make sure you know where Xpress is installed. The **path** will come handy for you at a later stage.

      
5. Tick the box “Yes, install the Xpress Kalis Mosel addon” when asked
6. Add the Xpress path to the environment variables (**Important!**)
    - *For Windows*
        - **Manually add the 'XPRESSDIR\bin' to the Windows environment path** 
    
           You can directly type in 'system properties' in your search bar or open your control panel. Then follow the below instrucction to change your system variables.
           
           Control panel -> system -> advanced system settings -> system properties -> environment variables -> change system variables -> add YOUR_XPRESS_INSTALLATION_DIRECTORY (e.g. C:\xpressmp\bin)
           
           (see [here](https://learn.sparkfun.com/tutorials/configuring-the-path-system-variable/all) for a step-by-step illustration)
        
        - **Restart your laptop**

        - Now you are good to move to the next step!
        
    - *For Mac*
        - Open your terminal

        -  Type in ``export XPRESSDIR=YOUR_XPRESS_INSTALL_DIRECTORY`` and press Enter

            replace the ``YOUR_XPRESS_INSTALL_DIRECTORY`` with your own Xpress installation path
            
            The default path is "/Applications/FICO Xpress/Xpress Workbench.app/Contents/Recourses/xpressmp". 
            
            So the command for you can be ``export XPRESSDIR="/Applications/FICO Xpress/Xpress Workbench.app/Contents/Recourses/xpressmp"``
            
            One some Macs with Intel Chips, the path can be "/Applications/FICO Xpress/xpressmp" so you may have to type ``export XPRESSDIR="/Applications/FICO Xpress/xpressmp"``
            
           You may have to navigate the directories to find out where xpressmp directory is located on your machine and use the appropriate path
            
            
        - Check whether the path is set by typing in ``echo $XPRESSDIR`` and press Enter
           
            If you see your Xpress installation path echoed, you are good to move to the next step
            
        - **Keep this window open when you move to the next step!**

<!--         Type ``. /Applications/FICO\ Xpress/xpressmp/bin/xpvars.sh`` in your terminal. Follow the instructions [here](https://www.fico.com/fico-xpress-optimization/docs/latest/installguide/dhtml/chapinst1_sec_secmac.html) -->

## Install the Xpress Wrapper and the JuMP packages
*The wrapper allows you to use Xpress in your jupyter notebook*
1. Open Julia Command-Line 
    - *for Windows* 
    
      - Type 'Julia' in the windows search bar and then click on 'Julia 1.11.2'
     
    - *for Mac*
      
      - **Please use the same terminal window** from the last step (when you add the path to the environment variable)
      - Type in ``exec '/Applications/Julia-1.6.app/Contents/Resources/julia/bin/julia'`` and press Enter to start Julia
      - Then follow the following steps
      
3. Type in ``import Pkg`` and press Enter
4. Type in ``Pkg.add("Xpress")`` and press Enter. Wait for a while ([reference](https://github.com/jump-dev/Xpress.jl))
5. Type in ``Pkg.add("JuMP")`` and press Enter. Wait for a while ([reference](https://jump.dev/JuMP.jl/stable/installation/))
6. Type in ``Pkg.build("Xpress")`` and press Enter. Wait  for a while
7. Test if installed by typing ``using JuMP, Xpress``. If you see the return saying 'found lincense file', you are good to go! 

![Xpress wrapper installation success](https://github.com/dajwani/Optimisation-Module-Installations/blob/main/static/Install_success.PNG)


## Install Alternative Solver to FICO Xpress MP

*If you are having difficulty installing Xpress on your laptop, as an alternative you can use any LP/ILP solver that is supported within JuMP such as HiGHS, GLPK or SCS [extensive list here](https://jump.dev/JuMP.jl/stable/packages/solvers/). Some such as CPLEX and Gurobi may require setting up licences like Xpress so choose carefully!*

1. Type in ``import Pkg`` and press Enter
2. Type in ``Pkg.add("GLPK")`` and press Enter
3. Test if installed by typing ``using GLPK``
4 In future tutorials, be sure to include ``using GLPK`` at the start of each notebook and to include ``model= Model(GLPK.Optimizer)`` to set which solver to use.

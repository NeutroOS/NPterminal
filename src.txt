import os
import shutil
from distutils.dir_util import copy_tree
import time
import platform
import psutil
import wmi


commands = "cd\nmkdir\nhelp\nls\nexit\nquit\nrun\ncls\ndel\nrmfile\nrmall\nmkfile\nrfile\ncfile\ncdir\nrename\ncompiler\nnotepad\nifile\nrun\nlsdir\ntexteditor\nmv\nsrc\ncc\ncwd\ninternet\nsysinfo"
runlist = "NeutroText.exe\nNeutroArt.exe\nNeutroNet.exe\nNeutroMath.exe\nbagel.exe\nbounce.exe\nflappy.exe\nguess.exe\nlife.exe\npacman.exe\nsimonsays.exe\nsnake.exe\ntictactoe.exe"

dr = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
drives = ['%s:'%d for d in dr if os.path.exists('%s:'%d)]

def convert(list):
    return tuple(list)

pc = wmi.WMI()



thing = "n"
os.system("cmd /c cls")






while thing == "n":

    os.system('color 8a')
    cpath = os.getcwd()

    cmd = input(":~$ ")


    if cmd=="cd":
        try:
            chpath = input("cd: ")
            os.chdir(chpath)
        except:
            print("Could not change path. Check the path.")

    if cmd=="help":
        try:
            print(commands)
        except:
            print("ERROR")


    if cmd=="ls":
        try:
            print(os.listdir(os.getcwd()))
        except:
            print("Could not list.")

    if cmd=="exit":
            os.system('color 7')
            os.system("cmd /c cls")
            exit()

    if cmd=="quit":
            os.system('color 7')
            os.system("cmd /c cls")
            exit()

    if cmd=="run":
        try:
            print("\n'run' is a command that lets you launch applications and other things like '.py' files.\nHere are some preinstalled apps from the 'NeutroOS' application library and other fun things\n")
            print(runlist)

            run = input("run: ")
            os.system("cmd /c " + run)

        except:
            print("Could not run.")

    if cmd == "cls":
            try:
                os.system("cmd /c cls")
            except:
                print("ERROR")

    if cmd=="mkdir":
        try:
            dir1 = input("mkdir: ")
            os.mkdir(dir1)
            print("Made directory.")


        except:
            print("Could not create directory.")

    if cmd=="del":
        try:
            print("commands for deletion:\nrmfile: remove a single file\nrmall: remove tree.")
        except:
            print("ERROR")


    if cmd=="rmfile":
        try:
            rmfile = input("rmfile: ")
            os.remove(rmfile)
            print("Removed file.")

        except:
            print("Could not remove the file. Check the path.")


    if cmd=="rmall":
        try:
            rmall = input("rmall: ")
            shutil.rmtree(rmall)
            print("Removed tree.")

        except:
            print("Could not remove tree. Check the path.")

    if cmd=="mkfile":
        try:
            mkfile = input("mkfile: ")
            file1 = open(mkfile, "a")
            content = input("content: ")
            file1.write(content)


            file1.close()
            print("Created file.")
        except:
            print("Could not create file.")


    if cmd=="rfile":
        try:
            filetoopen = input("file: ")
            openfile = open(filetoopen, "r")
            print(openfile.read())

        except:
            print("Could not open file. Check the path.")

    if cmd=="cfile":
        try:
            file3 = input("file: ")
            file2 = input("destination: ")

            shutil.copy2(file3, file2)
            print("Coppied file.")
        except:
            print("Could not copy file. Check the path.")

    if cmd=="cdir":
        try:
            src = input("directory: ")
            dest = input("destination: ")

            copy_tree(src, dest)
            print("Coppied tree.")
        except:
            print("Could not copy tree. Check the path.")

    if cmd=="rename":
        try:
            source = input("source: ")
            newname = input("newname: ")

            os.rename(source, newname)
            print("Renamed.")
        except:
            print("Could not rename. Check the path.")

    if cmd=="compiler":
        try:
            os.system("cmd /c auto-py-to-exe")
            print("Opened.")
        except:
            print("Auto-py-to-exe is not installed on the system. Install python to the system then write 'pip install auto-py-to-exe' in the command line.")

    if cmd=="notepad":
        try:
            notepad = input("file: ")
            os.system("cmd /c notepad " + notepad)
            print("Opened.")
        except:
            print("Could not open notepad.")

    if cmd=="ifile":
        try:
            ifile = input("File path: ")
            shutil.copy2(ifile, "/NPterminal/install")
            print("File has been installed.")

        except:
            print("Must cd to the NPterminal directory")


    if cmd=="lsdir":
        try:

            lsdir = input("directory: ")
            print(os.listdir(lsdir))

        except:
            print("Could not list directory due to a path error.")

    if cmd == "texteditor":
        try:
            os.system("cmd /c NeutroText.exe")
            print("Opened.")
        except:
            print("Must cd to the NPterminal directory.")

    if cmd == "mv":
        try:
            destination = input("destination: ")
            source1 = input("source: ")
            shutil.move(source1,destination)
            print("Moved.")
        except:
            print("Could not move due to a path error.")

    if cmd == "src":
        try:
            filetoopen1 = "src.txt"
            openfile = open(filetoopen1, "r")
            print(openfile.read())
            openfile.close()
        except:
            print("Must cd to the NPterminal directory.")

    if cmd == "cc":
        try:
            os.system("cmd /c NeutroText.exe")
            print("Opened.")
        except:
            print("Must cd to the NPterminal directory.")

    if cmd == "cwd":
        try:
            cpath = os.getcwd()
            print(cpath)
        except:
            print("Could not print directory.")

    if cmd == "d":
        try:
            listdrives = convert(drives)
            print(listdrives)
        except:
            print("Could not print directory.")

    if cmd == "internet":
        try:
            os.system("cmd /c NeutroNet.exe")
        except:
            print("Could not print directory.")

    if cmd == "sysinfo":
        try:
            print(f"Architecture: {platform.architecture()}")
            print(f"Network name: {platform.node()}")
            print(f"Operating system: {platform.platform()}")
            print(f"Central processing unit: {pc.Win32_Processor()[0].name}")
            print(f"Total random access memory: {psutil.virtual_memory().total / 1024 / 1024 / 1024:.2f} GB")
            print(f"Graphics processing unit: {pc.Win32_VideoController()[0].name}")
        except:
            print("SysError")

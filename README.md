# LockedMee

import java.io.File;
import java.io.IOException;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;
import java.nio.file.*;

public class SortFileName {
	public static void addFile(String Filename)  
	{ 
		
	File file = new File("//home//doshiy57gmail//Documents/project//"+Filename); //initialize File object and passing path as argument  
	boolean result;  
	try   
	{  
	result = file.createNewFile();  
	if(result)        
	{  
	System.out.println("file created "+file.getCanonicalPath());  
	}  
	else  
	{  
	System.out.println("File already exist at location: "+file.getCanonicalPath());  
	}  
	}   
	catch (IOException e)   
	{  
	e.printStackTrace();     
	}         
	}  
	public static void searchFile(String Filename)  
	{     
	File file = new File("//home//doshiy57gmail//Documents/project//"+Filename); //initialize File object and passing path as argument  
	boolean result;  
	try   
	{  
	result = file.exists() ;//creates a new file  
	if(result)      // test if successfully created a new file  
	{  
	System.out.println("file is   present in path "+file.getCanonicalPath()); //returns the path string  
	}  
	else  
	{  
	System.out.println("File is not present: "+file.getCanonicalPath());  
	}  
	}   
	catch (IOException e)   
	{  
	e.printStackTrace();    //prints exception if any  
	}         
	}  
	public static void deleteFile(String Filename)
    {
        try
        {
            Files.deleteIfExists(Paths.get("//home//doshiy57gmail//Documents/project//"+Filename));
            
        }
        catch(NoSuchFileException e)
        {
            System.out.println("No such file/directory exists");
        }
        catch(DirectoryNotEmptyException e)
        {
            System.out.println("Directory is not empty.");
        }
        catch(IOException e)
        {
            System.out.println("Invalid permissions.");
        }
          
        System.out.println("Deletion successful.");
    }
	public static void mainMenu()
	{
		char x;
		Scanner sc = new Scanner(System.in);
		String Filename="";
		
		
		do
		{
			x='n';
			System.out.println("Enter A to add the file to the lis, D to delete the file, S to search the given file is present in list and N to sort the list");
			System.out.println("Enter c to close the application");
		char op = sc.next().charAt(0);
		int o = 0;
		switch (op) {
		case 'A':
			System.out.println("Enter the File name to be created");
			Filename=sc.next();
			addFile(Filename);
			break;
		case 'D':
			System.out.println("Enter the File name to be deleted");
			Filename=sc.next();
			deleteFile(Filename);
			break;
		case 'S':
			System.out.println("Enter the File name to be searched");
			Filename=sc.next();
			searchFile(Filename);
			break;
		case 'C':
			System.exit(0);
			break;
			
		case 'N':
			System.out.println("Return to the main context ");
			sortfile();
			break;
		default:
			System.out.println("You enter wrong input");
			break;
		}

		System.out.println("Do you want to continue...press y or n to quit");
		x= sc.next().charAt(0);
		
		if(x=='n' || x=='N')
		{
			System.exit(0);
			
		}
		else
		{
			x='n';
		}
	
	}while(x=='n' || x=='N');
	

	}
	
		public static void main(String[] args) {
			String s="";
			System.out.println("Welcome to File handling Java Application...");
			System.out.println("**********Developed by Doshi KY **********");
			System.out.println("Press y||Y||YES||Yes||yes to perform File operations....");
			Scanner sc=new Scanner(System.in);
			s=sc.next();
			if((s.equals("YES"))|| (s.equals("y")) || (s.equals("Y")) || (s.equals("Yes")) || (s.equals("yes")))
			{
				mainMenu();
			}
			else
			{
				System.out.println("Exit from the application");
				System.exit(0);
			}
				}



		
		
			
			public static void sortfile()
			{
		File fileDir = new File("//home//doshiy57gmail//Documents/project//");
		if(fileDir.isDirectory()){
			List<String> listFile = Arrays.asList(fileDir.list());
			System.out.println("Listing files unsorted");
		
			for(String s:listFile){
				System.out.println(s);
			}
			Collections.sort(listFile);
			System.out.println("---------------------------------------");
			System.out.println("Sorting by filename in ascending order");
			for(String s:listFile){
				System.out.println(s);
			}
			System.out.println("---------------------------------------");
			System.out.println("Sorting by filename in descending order");
			Collections.sort(listFile,Collections.reverseOrder());
			for(String s:listFile){
				System.out.println(s);
			}

		}
		else{
			System.out.println(fileDir.getAbsolutePath() + " is not a directory");
		}
			}

	}

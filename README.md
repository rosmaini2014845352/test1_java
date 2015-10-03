*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package test1_itt786_rosmaini;

import java.io.IOException;
import java.nio.file.FileSystems;
import java.nio.file.Files;
import java.nio.file.StandardOpenOption;

public class Test1_itt786_rosmaini {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        String fn = "rosmaini_binary.txt";
	String rfn = "rosmaini_reverse_binary.txt";
	String fc = "Name\t:\tRosmaini binti Dollah\nMatrix No\t:\t2014845352\nGender\t:\tFemale\nAge\t:\t35 years old\nEmail\t:\trosmainidollah79@gmail.com\n";
		
	Test1_itt786_rosmaini a1 = new Test1_itt786_rosmaini();
		
		//Call method to write string
		a1.writeFile(fn,fc);
		
		//Call method to read file and write to another file in reverse order
		a1.writeReverse(rfn,a1.readFile(fn));

	}
	
	public void writeFile(String filename, String filecontent){
		try {
			System.out.println("Writing!");
			Files.write( FileSystems.getDefault().getPath(".", filename), 
			        filecontent.getBytes(), 
			        StandardOpenOption.CREATE);
			System.out.println("Done!");
		} catch (IOException e) {
			e.printStackTrace();
		}
		
	}
	
	public void writeReverse(String filename, byte [] filecontent){
		String[] sentenceList = new String(filecontent).split("\n");
		String reverseContent="";
		for(int i =sentenceList.length-1; i >=0; i--){
			reverseContent=reverseContent+sentenceList[i]+"\n";
		}
		try {
			System.out.println("Writing Reverse!");
			Files.write( FileSystems.getDefault().getPath(".", filename), 
					reverseContent.getBytes(), 
			        StandardOpenOption.CREATE);
			System.out.println("Done Write Reverse!");
		} catch (IOException e) {
			e.printStackTrace();
		}		
		
	}
	
	public byte[] readFile(String filename){
		byte[] content = null;
		try {
			content = Files.readAllBytes(FileSystems.getDefault().getPath(".", filename));
		} catch (IOException e) {
			e.printStackTrace();
		}
		return content;// TODO code application logic here
    }
    
}

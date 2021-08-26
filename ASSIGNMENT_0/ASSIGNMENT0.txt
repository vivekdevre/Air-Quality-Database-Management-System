import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;  
import java.io.IOException;
public class Read_data_from_csv {

	public static void main(String[] args) throws IOException {
		String line = "";  
		String splitBy = ",";
		int runs_scored=0;
		int i=0;
		int six_four=0;
		int balls=0;
		int warner_balls=0,warner_runs=0,warner_boundaries=0,warner_outs=0;
		BufferedReader br = new BufferedReader(new FileReader("C:\\Users\\kmsha\\Downloads\\deliveries.csv"));  
		while ((line = br.readLine()) != null)   
		{  
		String[] shot = line.split(splitBy);
		if(i==0) { 
			i++;
			continue;}
		int runs=Integer.parseInt(shot[17]);
		int over=Integer.parseInt(shot[4]);
		if (over>15) {
			if (runs==4 | runs==6) {
				six_four++;
			}
		runs_scored=runs_scored+runs;
		balls++;
		}
		
		if(shot[6].compareTo("DA Warner")==0) {
			warner_balls++;
			warner_runs=warner_runs+Integer.parseInt(shot[15]);
			if (shot[15]=="4" | shot[15]=="6") {
				warner_boundaries++;
			}
			if (shot.length==20) {
				warner_outs++;
			}
		}
		}
		System.out.println("Number of boundaries(6s & 4s) in last 4 overs="+six_four);
		System.out.println("Net run rate in last 4 overs is "+((runs_scored*6.0)/balls)+" runs.\n");
		System.out.println("David Warner IPL stats\n");
		System.out.println("Balls Faced "+warner_balls);
		System.out.println("Runs Scored "+warner_runs);
		System.out.println("Boundaries "+warner_boundaries);
		System.out.println("Times out "+warner_outs);
		System.out.println("Strike rate "+((double)warner_runs/warner_balls)*100);
		
		
	}

}
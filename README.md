# yaris
import java.util.Scanner;

public class Main {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		System.out.println("Bir tuşa basın  ");
		scanner.nextLine();
		
		ThreadRace race = new ThreadRace();
		race.addMainArray();
		race.simpleList(4);
		
		
		Runnable runnable1 = () -> race.threadRace(0);
		Thread thrace1 = new Thread(runnable1);
		
		Runnable runnable2 = () -> race.threadRace(1);
		Thread thrace2 = new Thread(runnable2);
		
		Runnable runnable3 = () -> race.threadRace(2);
		Thread thrace3 = new Thread(runnable3);
		
		Runnable runnable4 = () -> race.threadRace(3);
		Thread thrace4 = new Thread(runnable4);
		
		thrace2.start();
		thrace1.start();
		thrace4.start();
		thrace3.start();
		
		
		try {
			thrace2.join();
			thrace3.join();
			thrace4.join();
			thrace1.join();
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		
		try {
			Thread.sleep(6000);
		} catch (InterruptedException e) {
			e.printStackTrace();
			
		}
      race.info();
	}

}

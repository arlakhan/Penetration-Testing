![image](https://github.com/arlakhan/Penetration-Testing/assets/22939001/9ec50393-546d-4c27-a91f-0193f4427fe3)


This work collects the different IP address of different nodes such as client devices, edge nodes and cloud. This system checked the validity of IP address based on penetration Testing methods as determined in the following code. 


![image](https://github.com/arlakhan/Penetration-Testing/assets/22939001/eacb1aff-c34c-4311-b8dd-b7098bc470b9)






import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.net.InetAddress;

public class PenetrationTesting {

    public static void main(String[] args) {
        String txtFile = "Targets.txt";

        try (BufferedReader br = new BufferedReader(new FileReader(txtFile))) {
            String ipAddress;
            while ((ipAddress = br.readLine()) != null) {
                System.out.println("Testing target IP: " + ipAddress);
                boolean reachable = isHostReachable(ipAddress, 5000);
                System.out.println("Target " + ipAddress + " is " + (reachable ? "reachable" : "not reachable"));
            }

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    public static boolean isHostReachable(String ipAddress, int timeout) {
        try {
            InetAddress inet = InetAddress.getByName(ipAddress);
            return inet.isReachable(timeout);
        } catch (IOException e) {
            e.printStackTrace();
            return false;
        }
    }
}

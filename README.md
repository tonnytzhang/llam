import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

public class GetRequestWithCookiesExample {

    public static void main(String[] args) throws IOException {
        // URL of the resource you want to access
        String urlString = "http://example.com";

        // Set up the URL and open a connection
        URL url = new URL(urlString);
        HttpURLConnection connection = (HttpURLConnection) url.openConnection();

        // Set request method to GET
        connection.setRequestMethod("GET");

        // Add cookies to the request
        connection.setRequestProperty("Cookie", "cookieName=cookieValue");

        // Get the response code
        int responseCode = connection.getResponseCode();
        System.out.println("Response Code: " + responseCode);

        // Read and print the response content
        BufferedReader reader = new BufferedReader(new InputStreamReader(connection.getInputStream()));
        String line;
        StringBuilder responseContent = new StringBuilder();
        while ((line = reader.readLine()) != null) {
            responseContent.append(line);
        }
        reader.close();

        System.out.println("Response Content:");
        System.out.println(responseContent.toString());

        // Close the connection
        connection.disconnect();
    }
}

# web-customer-tracker
## spring mvc project no. 1

**how to check MySql DB connection? see the following:**

---

import java.io.IOException;  
import java.io.PrintWriter;  
import java.sql.Connection;  
import java.sql.DriverManager;  

import javax.servlet.ServletException;  
import javax.servlet.annotation.WebServlet;  
import javax.servlet.http.HttpServlet;  
import javax.servlet.http.HttpServletRequest; 
import javax.servlet.http.HttpServletResponse;     

/**
 * Servlet implementation class TestDbServlet
 */
@WebServlet("/TestDbServlet")
public class TestDbServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		
		// setup connections variables
		String user = "root";
		String pass = "";
		
		String jdbcUrl = "jdbc:mysql://localhost:3306/web_customer_tracker?useSSL=false";
		String driver = "com.mysql.jdbc.Driver";
		
		
		// get connection to database
		try {
			
			PrintWriter out = response.getWriter();
			out.println("Connection to database" + jdbcUrl);
			Class.forName(driver);
			Connection myConn = DriverManager.getConnection(jdbcUrl, user, pass);
			out.println("SUCCESS!");
			myConn.close();
			
			
		}catch(Exception e) {
			e.printStackTrace(); 
			throw new ServletException(e);
		}
	}

	

}

---



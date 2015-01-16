# Sistema-trade-1
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package trade.Conexion;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

/**
 *
 * @author .LENOVO
 */
public class AccesoBD_trade {

    private Connection connection = null;
    private static AccesoBD_trade instance = null;

    public static AccesoBD_trade getInstance() {
        if (instance == null) {
            instance = new AccesoBD_trade();
        }
        return instance;
    }

    public static java.sql.Connection GetConnection() throws ClassNotFoundException, SQLException {

        Connection conexion = null;
        String driver = "com.mysql.jdbc.Driver";
        String urlJDBC = "jdbc:mysql://localhost:3306/bd_trade";
        String usr = "root";
        String psw = "root";

        Class.forName(driver);
        return DriverManager.getConnection(urlJDBC, usr, psw);

    }

    @Override
    protected void finalize() throws Throwable {
        if (connection.isClosed()) {
            connection.close();
            connection = null;
        }
        super.finalize();
    }

}

# Delete_Update_Read-JDBC

package in.sp.test;

import java.sql.*;

public class CRUD_Operations {
    public static void main(String[] args) {

        try {
            Class.forName("com.mysql.cj.jdbc.Driver");

        } catch ( ClassNotFoundException e){
            e.printStackTrace();
        }

        String url = "jdbc:mysql://127.0.0.1:3306/crud_demo";
        String username = "root";
        String password = "Jordan@22@sql";

        //insertion query!!
//        String query = "insert into crud values (?, ?, ?, ?)";

        // deletion query!!
//        String query = "delete from crud where id = ? ";

        //update query
//        String query = "update crud set name = ?, age = ? , gender = ? where id = ? ";

        //read query
        String query = "Select * from crud;";

//        int id = 103;
//        String name = "Rajesh";
//        int age = 45;
//        String gender = "Male";
//        int value_to_delete = 106;

        try {
            Connection connection = DriverManager.getConnection(url, username, password);
            PreparedStatement preparedStatement = connection.prepareStatement(query);
//            preparedStatement.setInt(1, value_to_delete);

//            preparedStatement.setString(1, name);
//            preparedStatement.setInt(2, age);
//            preparedStatement.setString(3, gender);
//            preparedStatement.setInt(4, id);

//            preparedStatement.setInt(1, id);
//            preparedStatement.setString(2, name);
//            preparedStatement.setInt(3, age);
//            preparedStatement.setString(4, gender);

//            int i = preparedStatement.executeUpdate();
//            if (i>0){
//                System.out.println("Success.");
//            } else {
//                System.out.println("Failed.");
//            }
//            if (i>0){
//                System.out.println("Deleted Successfully.");
//            } else {
//                System.out.println("Failed.");
//            }
//            if (i>0){
//                System.out.println("Updated Successfully.");
//            } else {
//                System.out.println("Failed.");
//            }
            ResultSet resultSet = preparedStatement.executeQuery();

            while (resultSet.next()){

                int id = resultSet.getInt("id");
                System.out.println("Id : " + id);

                String name = resultSet.getString("name");
                System.out.println("Name : " + name);

                int age = resultSet.getInt("age");
                System.out.println("Age : " + age);

                String gender = resultSet.getString("gender");
                System.out.println("Gender : " + gender);

                System.out.println("========================");
            }
            connection.close();

        } catch (SQLException e){
            e.printStackTrace();
        }
    }
}

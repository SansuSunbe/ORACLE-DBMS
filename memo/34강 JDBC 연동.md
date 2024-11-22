# 34강 JDBC 연동

# DAO란?

- Data Access Object
- DB에 접근하여 DRUD를 하는 역할을 맡는 객체

# DB 연동하기

```sql
package dao;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DBConnecter {
	public static Connection getConnection() {
		Connection conn = null;
		
		try {
			String url = "jdbc:oracle:thin:@localhost:1521:XE";
			String user = "hr";
			String pw = "hr";
			Class.forName("oracle.jdbc.driver.OracleDriver");
			conn = DriverManager.getConnection(url, user, pw);
		} catch (ClassNotFoundException e) {
			
			e.printStackTrace();
		}  catch (SQLException e) {
			
			e.printStackTrace();
		}  catch (Exception e) {
			
			e.printStackTrace();
		} 
		return conn;
	}
}

```

# VO(Value Object) 생성

- 데이터를 받을 클래스 생성

```sql
package vo;

//NUM NUMBER,
//ID VARCHAR2(200),
//PW VARCHAR2(200),
//NAME VARCHAR(200),
//AGE NUMBER,
public class TBL_MEMBER_VO {
	private int number;
	private String id;
	private String pw;
	private String name;
	private int age;

	public int getNumber() {
		return number;
	}

	public void setNumber(int number) {
		this.number = number;
	}

	public String getId() {
		return id;
	}

	public void setId(String id) {
		this.id = id;
	}

	public String getPw() {
		return pw;
	}

	public void setPw(String pw) {
		this.pw = pw;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

}
```

# 중복검사 로직

```sql
package dao;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class TBL_MEMBER_DAO {

	Connection conn;
	PreparedStatement pstm;
	ResultSet rs;

	// 중복검사
	// 사용자가 입력한 아이디를 전달받음
	public boolean checkId(String id) {
		String query = "SELECT COUNT(ID) FROM TBL_MEMBER WHERE = ID = ?";
		boolean check = false;
		try {
			conn = DBConnecter.getConnection();
			pstm = conn.prepareStatement(query);
			pstm.setString(1, id); // ?에 아이디 값이 자동 삽입
			pstm.executeQuery();

			rs.next();
			if (rs.getInt(1) == 0) {
				check = true;
			}
			; // 0 또는 1 즉 중복 검사

		} catch (SQLException e) {

			e.printStackTrace();
		} finally {
			try {
				if (rs != null) {
					rs.close();
				}
				if (pstm != null) {
					pstm.close();
				}
				if (conn != null) {
					conn.close();
				}
			} catch (SQLException e) {
				throw new RuntimeException();
			}
		}
		return check;
	}
	// 회원가입
	// 로그인

}
```
# 简介
官方文档：http://mybatis.org/generator/index.html

#### 修改配置信息
##### generatorConfig.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE generatorConfiguration
  PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
  "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">

<generatorConfiguration>
	<context id="testTables" targetRuntime="MyBatis3">
		<commentGenerator>
			<!-- 是否去除自动生成的注释 true：是 ： false:否 -->
			<property name="suppressAllComments" value="true" />
		</commentGenerator>
		<!--数据库连接的信息：驱动类、连接地址、用户名、密码 -->
		<jdbcConnection driverClass="com.mysql.jdbc.Driver"
			connectionURL="jdbc:mysql://localhost:3306/hrms" userId="root"
			password="123456">
		</jdbcConnection>
		<!-- <jdbcConnection driverClass="oracle.jdbc.OracleDriver"
			connectionURL="jdbc:oracle:thin:@127.0.0.1:1521:demo"
			userId="SCOTT"
			password="tiger">
		</jdbcConnection> -->

		<!-- 默认false，把JDBC DECIMAL 和 NUMERIC 类型解析为 Integer，为 true时把JDBC DECIMAL 和 
			NUMERIC 类型解析为java.math.BigDecimal -->
		<javaTypeResolver>
			<property name="forceBigDecimals" value="false" />
		</javaTypeResolver>

		<!-- targetProject:生成PO类的位置 -->
		<javaModelGenerator targetPackage="com.mybatis.mbg.entity"
			targetProject=".\src\main\java">
			<!-- enableSubPackages:是否让schema作为包的后缀 -->
			<property name="enableSubPackages" value="false" />
			<!-- 从数据库返回的值被清理前后的空格 -->
			<property name="trimStrings" value="true" />
		</javaModelGenerator>
        <!-- targetProject:mapper映射文件生成的位置 -->
		<sqlMapGenerator targetPackage="com.mybatis.mbg.mapper"
			targetProject=".\src\main\java">
			<!-- enableSubPackages:是否让schema作为包的后缀 -->
			<property name="enableSubPackages" value="false" />
		</sqlMapGenerator>
		<!-- targetPackage：mapper接口生成的位置 -->
		<javaClientGenerator type="XMLMAPPER"
			targetPackage="com.mybatis.mbg.mapper"
			targetProject=".\src\main\resources">
			<!-- enableSubPackages:是否让schema作为包的后缀 -->
			<property name="enableSubPackages" value="false" />
		</javaClientGenerator>
		<!-- 生成对应表及类名 ,tableName:数据库表名,domainObjectName:实体名-->
		<table tableName="hrms_user" domainObjectName="HrmsUser"></table>
		<!-- 不生成Example类
		<table tableName="user_info" domainObjectName="UserInfo"
               enableCountByExample="false"
               enableUpdateByExample="false"
               enableDeleteByExample="false"
               enableSelectByExample="false"
               selectByExampleQueryId="false">
        </table>-->
		<!-- 有些表的字段需要指定java类型
		 <table schema="" tableName="">
			<columnOverride column="" javaType="" />
		</table> -->
	</context>
</generatorConfiguration>

```

修改点1：数据库配置
```
<jdbcConnection driverClass="com.mysql.jdbc.Driver"
	connectionURL="jdbc:mysql://localhost:3306/hrms" userId="root"
	password="123456">
</jdbcConnection>
```

修改点2：生成实体类存放位置
```
#com.mybatis.mbg.entity 可修改为自己项目映射目录
<javaModelGenerator targetPackage="com.mybatis.mbg.entity"
	targetProject=".\src\main\java">
	<!-- enableSubPackages:是否让schema作为包的后缀 -->
	<property name="enableSubPackages" value="false" />
	<!-- 从数据库返回的值被清理前后的空格 -->
	<property name="trimStrings" value="true" />
</javaModelGenerator>
```

修改点3：生成mapping文件存放位置
```
#targetPackage 包名可以修改
<sqlMapGenerator targetPackage="com.mybatis.mbg.mapper"
	targetProject=".\src\main\java">
	<!-- enableSubPackages:是否让schema作为包的后缀 -->
	<property name="enableSubPackages" value="false" />
</sqlMapGenerator>
```

修改点4：生成mapper接口存放位置
```
#targetPackage 目录可修改
<javaClientGenerator type="XMLMAPPER"
	targetPackage="com.mybatis.mbg.mapper"
	targetProject=".\src\main\resources">
	<!-- enableSubPackages:是否让schema作为包的后缀 -->
	<property name="enableSubPackages" value="false" />
</javaClientGenerator>
```

修改点5：生成对应表及类名
```
#对应自己的表信息（可copy多个）
<table tableName="hrms_user" domainObjectName="HrmsUser"></table>
```


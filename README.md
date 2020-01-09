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
    <!-- 数据库驱动 -->
    <classPathEntry    location="mysql-connector-java-5.1.9.jar"/>
    <context id="DB2Tables"    targetRuntime="MyBatis3">
        <commentGenerator> 
            <property name="suppressDate" value="true"/>
            <property name="suppressAllComments" value="true"/>
        </commentGenerator>
		<jdbcConnection driverClass="com.mysql.jdbc.Driver"
			connectionURL="数据库URL" userId="数据库用户名" password="数据库密码">
        </jdbcConnection>
		<!-- 数据库类型与java类型转换 -->
        <javaTypeResolver>
            <property name="forceBigDecimals" value="false"/>
        </javaTypeResolver>
        <!-- 生成Model类存放位置 -->
        <javaModelGenerator targetPackage="com.itunion.wxshop.model" targetProject="src">
            <property name="enableSubPackages" value="true"/>
            <property name="trimStrings" value="false"/>
        </javaModelGenerator>
        <!-- 生成映射文件存放位置 -->
        <sqlMapGenerator targetPackage="mapping" targetProject="src">
            <property name="enableSubPackages" value="true"/>
        </sqlMapGenerator>
        <!-- 生成Dao类存放位置 -->
        <javaClientGenerator type="XMLMAPPER" targetPackage="com.itunion.wxshop.mapper" targetProject="src">
            <property name="enableSubPackages" value="true"/>
        </javaClientGenerator>
        <!-- 生成对应表及类名 -->
        <table tableName="user_info" domainObjectName="UserInfo"
               enableCountByExample="false"
               enableUpdateByExample="false"
               enableDeleteByExample="false"
               enableSelectByExample="false"
               selectByExampleQueryId="false">
        </table>
    </context>
</generatorConfiguration>

```

修改点1：数据库配置
```
<jdbcConnection driverClass="com.mysql.jdbc.Driver"
            connectionURL="数据库URL" userId="数据库用户名" password="数据库密码">
        </jdbcConnection>
```

修改点2：生成model类存放位置
```
#com.itunion.wxshop.model 可修改为自己项目映射目录
<javaModelGenerator targetPackage="com.itunion.wxshop.model" targetProject="src">
            <property name="enableSubPackages" value="true"/>
            <property name="trimStrings" value="false"/>
        </javaModelGenerator>
```

修改点3：生成mapping文件存放位置
```
#targetPackage 报名可以修改
<!-- 生成映射文件存放位置 -->
        <sqlMapGenerator targetPackage="mapping" targetProject="src">
            <property name="enableSubPackages" value="true"/>
        </sqlMapGenerator>
```

修改点4：生产Dao类存放位置
```
#targetPackage 目录可修改
<javaClientGenerator type="XMLMAPPER" targetPackage="com.itunion.wxshop.mapper" targetProject="src">
            <property name="enableSubPackages" value="true"/>
        </javaClientGenerator>
```

修改点5：生成对应表及类名
```
#对应自己的表信息（可copy多个）
<table tableName="user_info" domainObjectName="UserInfo"></table>
```


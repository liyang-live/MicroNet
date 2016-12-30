# MicroNet（常用方法集合）
<h1>一、常用公共方法</h1>
<h1>二、项目目录介绍</h1>
<h3>1、MicroNet：适用于.Net Framework 4.0+的版本</h3>
<h3>2、MicroNetCore:适用.Net netstandard1.6版本</h3>
<h3>3、Test:单元测试项目</h3>
<h1>项目命名空间介绍:</h1>
<h3>1、MicroNet.Logging<br/></h3>
<h5>该名称空间下为日志帮助类,使用时以Logger点扩展方法使用,当Net Framework版本为4.5及以上时将会自动记录代码行数及源代码文件</h5>
<h3>2、MicroNet.SQLHelpers</h3>
<h5>该名称下为常用的数据库执行CRUD帮助类</h5>
<span>使用方法：<br/>
           连接字符串：  <add name="Constr" connectionString="Data Source=*/orcl;Persist Security Info=True;User ID=*;Password=*;"
      providerName="Oracle.ManagedDataAccess.Client"/><br/>
      
      注：该方法会自动根据转入的连接字符串的名称获取providerName 进行判断数据库类型，所有执行方法均使用ADO.Net标准方法<br/>
     
           SQLHelper db = new SQLHelper("Constr");<br/>
            /*一般语句执行*/<br/>
           var data = db.Instance.GetData("select * from tablename");<br/>
           /*存储过程执行*/<br/>
           OracleParameter[] OracleParameters = {<br/>
                        new OracleParameter("p_BQID", OracleDbType.Varchar2,200,"8001",ParameterDirection.Input),<br/>
                        new OracleParameter("P_UID", OracleDbType.Varchar2,200,"6666",ParameterDirection.Input),<br/>
                        new OracleParameter("P_KIND", OracleDbType.Char,200,"0",ParameterDirection.Input),<br/>
                        new OracleParameter("P_CUR", OracleDbType.RefCursor, ParameterDirection.Output)<br/>
                    };<br/>
<br/>
            var drug = db.Instance.ExecuteStor("proc_test", OracleParameters);
            <br/>
            /*返回实体*/<br/>
            var model = db.Instance.GetData<Advice>("select * from tablename");
            
<span>


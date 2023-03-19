# SQL_Server

# Realizando a criação de um usuário concedendo a ele função de sysadmin usando T-SQL

USE master;
GO

CREATE LOGIN [silas.sousa_usu] WITH PASSWORD = '#Dg40@27as';

ALTER SERVER ROLE sysadmin ADD MEMBER [silas.sousa_usu];
GO


<h1>Após criação efetuado consulta SQL retornando que o usuário foi criado com sucesso.</h1>


SELECT 
    sp.name AS login_name, 
    sr.name AS role_name
FROM 
    sys.server_principals sp
    LEFT JOIN sys.server_role_members srm ON sp.principal_id = srm.member_principal_id
    LEFT JOIN sys.server_principals sr ON srm.role_principal_id = sr.principal_id
WHERE 
    sp.type_desc IN ('SQL_LOGIN', 'WINDOWS_LOGIN', 'WINDOWS_GROUP')
	AND sp.name = 'silas.sousa_usu'
ORDER BY 
    login_name, role_name;
    
    
   ![image](https://user-images.githubusercontent.com/69328711/226206096-01813ca5-774f-4139-be4d-c4c8ae97310d.png)

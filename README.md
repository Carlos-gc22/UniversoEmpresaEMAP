# UniversoEmpresaEMAP
create database EMAPSA;

	create table empresaq(
	RUC int primary key not null,
	nombre varchar(20),
	direccion varchar(50),
	telefono int,
	correo varchar(50),
	sitioweb varchar(50));

	create table descrpago(
	id_pago int primary key not null,
	nombre_mes varchar(20),
	aano varchar(20),
	nombre_pago varchar(20),
	total decimal(6,2));

	create table facturap(
	id_factura int primary key not null,
	fecha_pago date,
	total_pago decimal(6,2));

	create table empleados(
	cedula_empleado int primary key not null,
	nombre varchar (20),
	apellido varchar(20),
	telefono int,
	direccion_e varchar(40),
	fecha_ing date,
	RUCpk int
	foreign key(RUCpk) references empresaq(RUC));

	create table clientes(
	cedula_cliente int primary key not null,
	nombres varchar(50),
	apellidos varchar(50),
	telefono int,
	sector_vive varchar(40),
	tiene_convenio varchar(5),
	id_pagopk int,
	foreign key (id_pagopk) references descrpago(id_pago));

	create table medidores(
	numero_medidor varchar(15) primary key not null,
	consumo_agua varchar(10),
	numero_lote varchar(10),
	cedula_empleadopk int,
	cedula_clientepk int,
	foreign key (cedula_empleadopk) references empleados(cedula_empleado),
	foreign key (cedula_clientepk) references clientes(cedula_cliente));

	
	create table detallefacturas(
	Nfactura varchar(20) primary key not null,
	total_convenio decimal(6,2),
	ts_alcantarillado decimal(6,2),
	cedula_clientepk int,
	cedula_empleadopk int,
	RUCpk int,
	numero_medidorpk varchar(15),
	id_facturapk int,
	foreign key (cedula_clientepk) references clientes(cedula_cliente),
	foreign key (cedula_empleadopk) references empleados(cedula_empleado),
	foreign key (RUCpk) references empresaq(RUC),
	foreign key (numero_medidorpk) references medidores(numero_medidor),
	foreign key (id_facturapk) references facturap(id_factura));

	insert into empresaq(RUC,nombre,direccion,telefono,correo,sitioweb) values
	(1313001,'EMAP','Av.La cultura y calle 13',052365987,'emap@gmail.com','www.emap.com');
	select * from empresaq;

	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(101,'Enero','2020','Deuda',50.49)
	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(102,'Marzo','2020','Deuda',100.00)
	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(103,'Febrero','2020','Pagado',30.15)
	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(104,'Enero','2020','Deuda',80.20)
	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(105,'Marzo','2020','Deuda',23.56)
	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(106,'Enero','2020','Pagado',78.99)
	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(107,'Febrero','2020','Pagado',10.79)
	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(108,'Abril','2020','Pagado',55.90)
	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(109,'Marzo','2020','Pagado',220.71)
	insert into descrpago(id_pago,nombre_mes,aano,nombre_pago,total) values
	(110,'Enero','2020','Pagado',64.22)
	select * from descrpago;

	insert into facturap(id_factura,fecha_pago,total_pago) values
	(001,'2020-10-08',23.12);
	insert into facturap(id_factura,fecha_pago,total_pago) values
	(002,'2020-09-08',9.78);
	insert into facturap(id_factura,fecha_pago,total_pago) values
	(003,'2020-11-08',10.45);
	insert into facturap(id_factura,fecha_pago,total_pago) values
	(004,'2020-10-08',45.50);
	insert into facturap(id_factura,fecha_pago,total_pago) values
	(005,'2020-10-08',25.65);
	insert into facturap(id_factura,fecha_pago,total_pago) values
	(006,'2020-11-08',17.89);
	insert into facturap(id_factura,fecha_pago,total_pago) values
	(007,'2020-10-08',30.23);
	insert into facturap(id_factura,fecha_pago,total_pago) values
	(008,'2020-09-08',50.61);
	insert into facturap(id_factura,fecha_pago,total_pago) values
	(009,'2020-11-08',37.05);
	insert into facturap(id_factura,fecha_pago,total_pago) values
	(010,'2020-10-08',19.99);
	select * from facturap;

	insert into empleados(cedula_empleado,nombre,apellido,telefono,direccion_e,fecha_ing,RUCpk) values
	(1313457898,'Julio','Castro',0990367673,'Las acacias','2010-09-12',1313001);
	insert into empleados(cedula_empleado,nombre,apellido,telefono,direccion_e,fecha_ing,RUCpk) values
	(1314673726,'Alberto','Pinargote',096788484,'Los Esteros','2011-07-01',1313001);
	insert into empleados(cedula_empleado,nombre,apellido,telefono,direccion_e,fecha_ing,RUCpk) values
	(1389009881,'Juan','Macías',0983737373,'Santa Martha','2009-01-23',1313001);
	select * from empleados;

	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(131345677,'Elver Dorado','Castro Altamirano',0996777555,'Norte-Av.La Cultura','Sí',01);
	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(131535355,'Mauro Enrique','Pinargote Macías',0987857744,'Norte-El Guabito','No',02);
	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(131455543,'Rafael Antonio','Correa Castro',0988855711,'Centro-Calle 15','No',03);
	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(132367262,'Andrea Liz','Castillo Ortíz',0956656662,'Sur-San Mateo','No',04);
	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(132872278,'María Carmen','Ochoa Cruz',0977222111,'Sur-Av Barbasquillo','Sí',05);
	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(130988484,'Cirilo Andrés','Moreira Nepal',0984472344,'Centro-Santa Martha','Sí',06);
	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(132161091,'Derian Martín','España Hurtado',0985711220,'Norte-Las Cumbres','No',07);
	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(131762719,'Carlos Jesús','Zambrano Reyes',0974692821,'Sur-Las Orquideas','Sí',08);
	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(131727333,'Alex José','López Carrascal',0998746362,'Centro-El Rosal','Sí',09);
	insert into clientes(cedula_cliente,nombres,apellidos,telefono,sector_vive,tiene_convenio,id_pagopk) values
	(131618043,'Erick Alberto','Díaz Cedeño',0998484840,'Norte-La Proaño','Sí',10);
	select * from clientes;

	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('NM0011','1243M3','N172-3',1313457898,131345677);
	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('NM0012','537M3','N156-1',1313457898,131535355);
	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('NM0013','1509M3','N231-8',1313457898,132161091);
	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('NM0014','2340M3','N357-2',1313457898,131618043);
	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('NM0015','4562M3','N145-7',1314673726,132367262);
	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('MN0016','0112M3','N451-0',1314673726,132872278);
	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('MN0017','2411M3','N132-1',1314673726,131762719);
	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('MN0018','0232M3','N223-5',1389009881,131455543);
	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('MN0019','1261M3','N521-6',1389009881,130988484);
	insert into medidores(numero_medidor,consumo_agua,numero_lote,cedula_empleadopk,cedula_clientepk) values
	('MN0020','1003M3','N179-3',1389009881,131727333);
	select * from medidores;

	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F123001',10.00,1.50,131345677,1313457898,1313001,'NM0011',001);
	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F124002',null,1.50,131535355,1313457898,1313001,'NM0012',002);
	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F131003',null,1.50,131455543,1389009881,1313001,'MN0018',003);
	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F122004',null,1.50,132367262,1314673726,1313001,'NM0015',004);
	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F113005',20.00,1.50,132872278,1314673726,1313001,'MN0016',005);
	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F132006',10.00,1.50,130988484,1389009881,1313001,'MN0019',006);
	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F111007',null,1.50,132161091,1313457898,1313001,'NM0013',007);
	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F321008',10.00,1.50,131762719,1314673726,1313001,'MN0017',008);
	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F141009',20.00,1.50,131727333,1389009881,1313001,'MN0020',009);
	insert into detallefacturas(Nfactura,total_convenio,ts_alcantarillado,cedula_clientepk,cedula_empleadopk,RUCpk,numero_medidorpk,id_facturapk) values
	('F412010',10.00,1.50,131618043,1313457898,1313001,'NM0014',010);
	select * from detallefacturas;

	-- Se desea saber que clientes están al día con los pagos --
	   select id_pago,nombres,apellidos,sector_vive,nombre_mes,aano,nombre_pago,total from clientes
	   join descrpago on id_pago=id_pagopk where nombre_pago='Pagado' order by nombres asc; 

	-- Se desea saber que clientes están atrasado con los pagos --
	   select id_pago,nombres,apellidos,sector_vive,nombre_mes,aano,nombre_pago,total from clientes
	   join descrpago on id_pago=id_pagopk where nombre_pago='Deuda' order by nombres asc;

	-- Se desea saber que cliente consume más agua --
	   select numero_medidor,nombres,apellidos,sector_vive,consumo_agua,numero_lote from medidores
	   join clientes on cedula_cliente=cedula_clientepk where consumo_agua>'3330M3' order by nombres asc;

	-- Top de clientes que tienen convenio con la empresa --
	    select nombres,apellidos,sector_vive,tiene_convenio,total_convenio from detallefacturas
	   join clientes on cedula_cliente=cedula_clientepk where tiene_convenio='Sí' order by nombres asc; 

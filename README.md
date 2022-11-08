# CRUDBasico
Crud en C# para .net

Este seria el codigo para crear la base de datos 

create database Practica
go 
use Practica

create table Productos
(Id int identity (1,1) primary key,
Nombre nvarchar (100),
Descripcion nvarchar (100),
Marca nvarchar (100),
Precio float,
Stock int)

insert into Productos
values
('Gaseosa','3 litros','marcacola',7.5,24),
('Chocolate','Tableta 100 gramos','iberica',12.5,36)


----mostrar en tabla
create proc ESP_MostrarProductos
as
select*from Productos
go

-----INSERTAR
create proc ESP_InsertarProductos
@nombre nvarchar(100),
@descrip nvarchar(100),
@marca nvarchar(100),
@precio float,
@stock int
as
insert into Productos values (@nombre,@descrip,@marca,@precio,@stock)
go


-------ELIMINAR
create proc ESP_EliminarProducto
@idpro int 
as
delete from Productos where Id=@idpro
go

-------EDITAR
create proc EditarProductos
@nombre nvarchar(100),
@descrip nvarchar(100),
@marca nvarchar(100),
@precio float,
@stock int,
@id int
as
update Productos set Nombre=@nombre, Descripcion=@descrip, Marca=@marca, Precio=@precio, Stock=@stock where Id=@id
go

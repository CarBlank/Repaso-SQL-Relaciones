# Repaso-SQL-Relaciones

2.1.Crear diagrama
Crea un diagrama utilizando DBeaver de una base de datos de un e-commerce (tienda online) con las siguientes tablas:
Tabla Users
Tabla Products
Tabla Orders
Tabla Categories
Debe mostrar los tipos de relaciones entre cada tabla. \*Recuerda que en el caso de una relación muchos a muchos necesitarás una tabla intermedia.

CREATE TABLE `users` (
`id_users` int NOT NULL AUTO_INCREMENT,
`name` varchar(100) DEFAULT NULL,
`last_name` varchar(100) DEFAULT NULL,
PRIMARY KEY (`id_users`)
) ENGINE=InnoDB AUTO_INCREMENT=6 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

CREATE TABLE `categories` (
`id_categories` int NOT NULL AUTO_INCREMENT,
`name` varchar(100) DEFAULT NULL,
PRIMARY KEY (`id_categories`)
) ENGINE=In

CREATE TABLE `orders` (
`id_orders` int NOT NULL AUTO_INCREMENT,
`name` varchar(100) DEFAULT NULL,
PRIMARY KEY (`id_orders`)
) ENGINE=Inn

CREATE TABLE `orders` (
`id_orders` int NOT NULL AUTO_INCREMENT,
`name` varchar(100) DEFAULT NULL,
`id_user` int DEFAULT NULL,
PRIMARY KEY (`id_orders`),
KEY `orders_users_FK` (`id_user`),
CONSTRAINT `orders_users_FK` FOREIGN KEY (`id_user`) REFERENCES `users` (`id_users`)
) ENGINE

CREATE TABLE `products` (
`id_products` int NOT NULL,
`name` varchar(100) DEFAULT NULL,
`precio` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
PRIMARY KEY (`id_products`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

CREATE TABLE `orders_products` (
`id_orders` int DEFAULT NULL,
`id_products` int DEFAULT NULL,
KEY `orders_products_orders_FK` (`id_orders`),
KEY `orders_products_products_FK` (`id_products`),
CONSTRAINT `orders_products_orders_FK` FOREIGN KEY (`id_orders`) REFERENCES `orders` (`id_orders`),
CONSTRAINT `orders_products_products_FK` FOREIGN KEY (`id_products`) REFERENCES `products` (`id_products`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

2.2. Ejecute las siguientes consultas SQL
A continuación, deberá realizar las siguientes consultas SQL:

2.2.1 INSERTAR DATOS

Inserte al menos 5 nuevos usuarios.
Inserte al menos 5 nuevos productos.
Inserte al menos 5 nuevos pedidos(orders).
Inserte al menos 2 tipos de categorías.

insert into orders (name)
values
('00001'),
('00002'),
('00003');

insert into orders_products (id_orders , id_products)
values
(3 , 3),
(3 , 3);

SELECT p.name, o.name , p.id_products , o.id_orders
FROM orders_products op
INNER JOIN products p ON op.id_products = p.id_products
INNER JOIN orders o ON op.id_orders = o.id_orders

insert into users (name , last_name)
values
('Laura' , 'Sanchez'),
('Mario' , 'Garcia'),
('Ana' , 'Marin'),
('Sara', 'Rojas'),
('Alex' , 'Martin');

insert into categories (name)
values
('Baño'),
('Cocina');

2.2.2 ACTUALIZAR DATOS

Cambiar el nombre de un producto. Para ello, genera una consulta que afecte solo a un determinado producto en función de su id.
Cambiar el precio de un producto a 50€. Para ello, genera una consulta que afecte solo a un determinado producto en función de su id.

UPDATE products SET name = 'Cucharas' WHERE id_products = 1;

UPDATE products SET precio = '50€' WHERE id_products = 1;

2.2.3 OBTENER DATOS

Seleccione todos los productos con un precio superior a 20€.
Muestre de forma descendente los productos.
Seleccione todos los productos y que muestre la categoría a la que pertenecen.
Seleccione todos los usuarios y muestre sus pedidos.
Selecciona un producto por su id y que muestre la categoría a la que pertenece.
Seleccione a un usuario por su id y muestre los pedidos que tiene.

SELECT \* FROM products p WHERE precio > 20;

SELECT \* FROM products p ORDER BY id_products DESC;

SELECT p.name , c. name
FROM products p
INNER JOIN categories c ON p.id_products = c.id_categories

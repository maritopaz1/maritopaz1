- -- Tabla Usuarios
CREATE TABLE Usuarios (
    usuario_id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    correo VARCHAR(100) NOT NULL,
    contraseña VARCHAR(100) NOT NULL
);

-- Tabla Clientes
CREATE TABLE Clientes (
    cliente_id INT AUTO_INCREMENT PRIMARY KEY,
    usuario_id INT NOT NULL,
    nombre VARCHAR(100) NOT NULL,
    direccion VARCHAR(255),
    telefono VARCHAR(20),
    FOREIGN KEY (usuario_id) REFERENCES Usuarios(usuario_id)
);

-- Tabla Inventarios
CREATE TABLE Inventarios (
    inventario_id INT AUTO_INCREMENT PRIMARY KEY,
    producto VARCHAR(100) NOT NULL,
    cantidad INT NOT NULL,
    precio DECIMAL(10, 2) NOT NULL
);

-- Tabla Factura
CREATE TABLE Factura (
    factura_id INT AUTO_INCREMENT PRIMARY KEY,
    cliente_id INT NOT NULL,
    fecha DATE NOT NULL,
    total DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (cliente_id) REFERENCES Clientes(cliente_id)
);

-- Tabla Ventas
CREATE TABLE Ventas (
    venta_id INT AUTO_INCREMENT PRIMARY KEY,
    cliente_id INT NOT NULL,
    inventario_id INT NOT NULL,
    factura_id INT NOT NULL,
    fecha DATE NOT NULL,
    total DECIMAL(10, 2) NOT NULL,
    FOREIGN KEY (cliente_id) REFERENCES Clientes(cliente_id),
    FOREIGN KEY (inventario_id) REFERENCES Inventarios(inventario_id),
    FOREIGN KEY (factura_id) REFERENCES Factura(factura_id)
);


-- Inserciones en la tabla Usuarios
INSERT INTO Usuarios (nombre, correo, contraseña) VALUES 
('Juan Pérez', 'juan.perez@example.com', 'password123'),
('María López', 'maria.lopez@example.com', 'maria456'),
('Carlos Rodríguez', 'carlos.rod@example.com', 'carlos789'),
('Ana García', 'ana.garcia@example.com', 'ana321'),
('Luis Fernández', 'luis.fernandez@example.com', 'luis654');

-- Inserciones en la tabla Clientes
INSERT INTO Clientes (usuario_id, nombre, direccion, telefono) VALUES 
(1, 'Cliente A', 'Calle 123, Ciudad A', '555-1234'),
(2, 'Cliente B', 'Avenida 456, Ciudad B', '555-5678'),
(3, 'Cliente C', 'Plaza 789, Ciudad C', '555-9101'),
(4, 'Cliente D', 'Boulevard 101, Ciudad D', '555-1121'),
(5, 'Cliente E', 'Calle 202, Ciudad E', '555-3141');

-- Inserciones en la tabla Inventarios
INSERT INTO Inventarios (producto, cantidad, precio) VALUES 
('Producto 1', 100, 10.50),
('Producto 2', 200, 15.75),
('Producto 3', 150, 8.99),
('Producto 4', 250, 12.30),
('Producto 5', 300, 20.00);

-- Inserciones en la tabla Factura
INSERT INTO Factura (cliente_id, fecha, total) VALUES 
(1, '2024-08-01', 105.00),
(2, '2024-08-02', 157.50),
(3, '2024-08-03', 89.90),
(4, '2024-08-04', 123.00),
(5, '2024-08-05', 200.00);

-- Inserciones en la tabla Ventas
INSERT INTO Ventas (cliente_id, inventario_id, factura_id, fecha, total) VALUES 
(1, 1, 1, '2024-08-01', 105.00),
(2, 2, 2, '2024-08-02', 157.50),
(3, 3, 3, '2024-08-03', 89.90),
(4, 4, 4, '2024-08-04', 123.00),
(5, 5, 5, '2024-08-05', 200.00);

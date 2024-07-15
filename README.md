-- Crear la tabla clientes si no existe  
CREATE TABLE IF NOT EXISTS  clientes (
    id_cliente SERIAL PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    direccion TEXT NOT NULL,
    telefono VARCHAR(20),
    correo_electronico VARCHAR(100)
);

-- Crear la tabla paquetes si no existe  
CREATE TABLE paquetes (
    id_paquete SERIAL PRIMARY KEY,
    peso DECIMAL(10, 2) NOT NULL,
    dimensiones VARCHAR(50) NOT NULL,
    descripcion TEXT
);

--  Crear la tabla envíos si no existe 
CREATE TABLE envios (
    id_envio SERIAL PRIMARY KEY,
    fecha_envio DATE NOT NULL,
    fecha_estimada_entrega DATE,
    direccion_destino TEXT NOT NULL,
    estado VARCHAR(50) NOT NULL,
    id_cliente INT REFERENCES clientes(id_cliente)
);


--  Crear la tabla rutas si no existe 
CREATE TABLE rutas (
    id_ruta SERIAL PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    descripcion TEXT
    id_envio INT REFERENCES envios(id_envio),
    id_paquete INT REFERENCES paquetes(id_paquete),
    posicion INT NOT NULL
);


--  Crear la tabla de detalles de envío si no existe 
CREATE TABLE detalles_envio (
    id_detalle SERIAL PRIMARY KEY,
    fecha_registro TIMESTAMP
);

-- Insertar datos en la tabla de clientes
INSERT INTO clientes (nombre, direccion, telefono, correo_electronico) VALUES
('diego', 'Ixtapaluca', '123456789', 'diego@smart-force.com'),
 ('juan','Chalco', '234567890', 'juan@smart-force.com'),
 ('Guadalupe','San Francisco', '345678901', 'guadalupe@smart-force.com'),
 ('Luis Espeleta','Ixtapaluca', '456789012', 'luis.espeleta@smart-force.com'),
 ('Jovani','Chalco', '567890123', 'jovani@smart-force.com'),
 ('Carlos','Ayotla', '678901234', 'carlos@smart-force.com'),
 ('iban rodrigues','Ayotla', '789012345', 'ivan.rodriguez@smart-force.com'),
 ('Graciela','Ecatepec', '890123456', 'graciela@smart-force.com'),
 ('Brenda Leyte','Ecatepec', '901234567', 'brenda.leyte@smart-force.com'),
 ('Raúl parra', 'La paz', '012345678', 'raul.parra@smart-force.com'),
 ('Yolanda','Reyes', '123450987', 'yolanda@smart-force.com'),
 ('julio salvador', 'Reyes', '234561098', 'julio.salvador@smart-force.com'),
 ('Graciela','Izcalli', '345672109', 'graciela@smart-force.com'),
 ('Johan','Tecámac', '456783210', 'johan@smart-force.com'),
 ('Monserrat','Tecámac', '567894321', 'monserrat@smart-force.com'),
 ('cesar Gonzáles','Puebla', '678905432', 'cesar.gonzalez@smart-force.com'),
 ('Carlos Álvarez','Puebla ', '789016543', 'carlos.alvarez@smart-force.com'),
 ('Roberto','Cuatro vientos', '890127654', 'roberto@smart-force.com'),
 ('Ariel','Cuatro','901238765', 'ariel@smart-force.com'),
 ('Daniel Gonzáles', 'Texcoco', '012349876', 'daniel.gonzalez@smart-force.com');

-- Insertar datos en la tabla de clientes

INSERT INTO paquetes (peso, dimensiones, descripcion) VALUES
(2.5, '10x10x10', 'Paquete_pequeño'),
(5.0, '20x20x20', 'Paquete_mediano'),
(1.2, '5x5x5', 'Paquete_pequeño'),
(3.0, '15x15x15', 'Paquete_mediano'),
(7.5, '25x25x25', 'Paquete_grande'),
(4.0, '18x18x18', 'Paquete_mediano'),
(6.3, '22x22x22', 'Paquete_grande'),
(2.8, '12x12x12', 'Paquete_mediano'),
(8.1, '30x30x30', 'Paquete_grande'),
(1.9, '8x8x8', 'Paquete_pequeño'),
(3.5, '14x14x14', 'Paquete_mediano'),
(2.2, '9x9x9', 'Paquete_pequeño'),
(4.7, '17x17x17', 'Paquete_mediano'),
(5.9, '23x23x23', 'Paquete_grande'),
(6.8, '27x27x27', 'Paquete_grande'),
(3.3, '16x16x16', 'Paquete_mediano'),
(7.2, '28x28x28', 'Paquete_grande'),
(2.6, '11x11x11', 'Paquete_mediano'),
(4.1, '19x19x19', 'Paquete_mediano'),
(5.6, '21x21x21', 'Paquete_grande');

-- Insertar datos en la tabla de envíos
INSERT INTO envios (fecha_envio, fecha_estimada_entrega, direccion_destino, estado, id_cliente) VALUES
('2024-07-01', '2024-07-05','Ixtapaluca', 'en tránsito', 1),
('2024-06-02', '2024-06-06','Chalco', 'entregado', 2),
('2024-04-03', '2024-04-07','San Francisco', 'retrasado', 3),
('2024-07-04', '2024-07-08','Ixtapaluca', 'en tránsito', 4),
('2024-07-05', '2024-07-09','Chalco', 'entregado', 5),
('2024-07-06', '2024-07-10','Ayotla', 'retrasado', 6),
('2024-07-07', '2024-07-11','Ayotla', 'en tránsito', 7),
('2024-06-08', '2024-06-12','Ecatepec', 'entregado', 8),
('2024-06-09', '2024-06-13','Ecatepec', 'retrasado', 9),
('2024-06-10', '2024-06-14','La paz', 'en tránsito', 10),
('2024-04-11', '2024-04-15','Reyes', 'entregado', 11),
('2024-04-12', '2024-04-16','Reyes', 'retrasado', 12),
('2024-01-13', '2024-01-17','Izcalli', 'en tránsito', 13),
('2024-01-14', '2024-01-18','Tecámac', 'entregado', 14),
('2024-05-15', '2024-05-19','Tecámac', 'retrasado', 15),
('2024-05-16', '2024-05-20','Puebla', 'en tránsito', 16),
('2024-05-17', '2024-05-21','Puebla ', 'entregado', 17),
('2024-03-18', '2024-03-22','Cuatro vientos', 'retrasado', 18),
('2024-03-19', '2024-03-23','Cuatro', 'en tránsito', 19),
('2024-03-20', '2024-03-24','Texcoco', 'entregado', 20),
('2024-05-02', '2024-05-06','Chalco', 'entregado', 18),
('2024-07-09', '2024-07-13','Ecatepec', 'retrasado', 9),
('2024-06-02', '2024-06-06','Chalco', 'entregado', 9),
('2024-06-09', '2024-06-13','Ecatepec', 'retrasado', 18),
('2024-03-18', '2024-03-22','Cuatro vientos', 'retrasado', 18),
('2024-07-06', '2024-07-10','Ayotla', 'retrasado', 9),
('2024-07-06', '2024-07-10','Ayotla', 'retrasado', 18),
('2024-07-06', '2024-07-10','Ayotla', 'retrasado', 9),
('2024-03-19', '2024-03-23','Cuatro', 'en tránsito', 18),
('2024-03-20', '2024-03-24','Texcoco', 'entregado', 9),
('2024-05-16', '2024-05-20','Puebla', 'en tránsito', 18),
('2024-03-20', '2024-03-24','Texcoco', 'entregado', 9),
('2024-05-16', '2024-05-20','Puebla', 'en tránsito', 9)
('2024-06-02', '2024-06-06','Chalco', 'entregado', 18),
('2024-06-09', '2024-06-13','Ecatepec', 'retrasado', 9),
('2024-06-02', '2024-06-06','Chalco', 'entregado', 9),
('2024-06-09', '2024-06-13','Ecatepec', 'retrasado', 18),
('2024-03-18', '2024-03-22','Cuatro vientos', 'retrasado', 18);

-- Insertar datos en la tabla de rutas
INSERT INTO rutas (nombre, descripcion) VALUES
('Ixtapaluca', 'Cerro El Tezoyo'),
('Chalco', 'Cerro El Tejolote'),
('San Francisco', 'Cerro El Tejolote'),
('Ixtapaluca', 'Cerro El Tezoyo'),
('Chalco', 'Loma Bonita'),
('Ayotla', 'Nopalera'),
('Ayotla', 'Capulín'),
('Ecatepec', 'Bosques'),
('Ecatepec', 'Casuarina'),
('La paz', 'Cerca del metro'),
('Reyes', 'Bancos'),
('Reyes', 'Plaza de la tecnología'),
('Izcalli', 'Enfrente de las primarias'),
('Tecámac', 'Cedros'),
('Tecámac', 'olmos'),
('Puebla', 'volcanes '),
('Puebla ', 'san Andrés'),
('Cuatro vientos', 'La Bombilla'),
('Cuatro vientos', 'Ávila'),
('Texcoco', 'plaza Texcoco');


-- Insertar datos en la tabla de detalles de envío
INSERT INTO detalles_envio (id_envio, id_paquete, posicion) VALUES
(1, 2, 1),
(2, 2, 1),
(3, 1, 3),
(4, 1, 4),
(5, 2, 3),
(6, 6, 6),
(7, 6, 7),
(8, 6, 8),
(9, 8, 9),
(10, 20, 10),
(11, 11, 12),
(12, 12, 12),
(13, 13, 14),
(14, 14, 14),
(15, 18, 15),
(16, 19, 16),
(17, 16, 17),
(18, 18, 18),
(19, 17, 19),
(20, 19, 20);

---- Crear la tabla de auditoría

CREATE TABLE registro_envios (
    id_registro SERIAL PRIMARY KEY,
    id_envio INT,
    fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);


-- Crear la función que será llamada por el trigger
CREATE OR REPLACE FUNCTION registrar_envio()
RETURNS TRIGGER AS $$
BEGIN
    INSERT INTO registro_envios (id_envio, fecha_registro)
    VALUES (NEW.id_envio, CURRENT_TIMESTAMP);
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- -- Crear el trigger
CREATE TRIGGER after_envio_insert
AFTER INSERT ON envios
FOR EACH ROW
EXECUTE FUNCTION registrar_envio();

-- Crear el stored procedure
CREATE OR REPLACE PROCEDURE obtener_envios_por_cliente(IN id_cliente INT)
LANGUAGE plpgsql
AS $$
BEGIN
    SELECT *
    FROM envios
    WHERE id_cliente = id_cliente;
END;
$$;



-- Crear la función
CREATE OR REPLACE FUNCTION calcular_tiempo_envio(id_envio INT)
RETURNS INTERVAL AS $$
DECLARE
    tiempo_total INTERVAL;
BEGIN
    SELECT (fecha_estimada_entrega - fecha_envio) INTO tiempo_total
    FROM envios
    WHERE id_envio = id_envio;
    RETURN tiempo_total;
END;
$$ LANGUAGE plpgsql;

-- Consulta de clientes con más de 5 envíos en el último mes
SELECT c.id_cliente, c.nombre, COUNT(e.id_envio) AS total_envios
FROM clientes c
JOIN envios e ON c.id_cliente = e.id_cliente
WHERE e.fecha_envio >= DATE_TRUNC('month', CURRENT_DATE) - INTERVAL '1 month'
GROUP BY c.id_cliente, c.nombre
HAVING COUNT(e.id_envio) > 5;


-- Consulta del promedio de tiempo de entrega de los envíos completados
SELECT AVG(e.fecha_estimada_entrega - e.fecha_envio) AS promedio_tiempo_entrega
FROM envios e
WHERE e.estado = 'entregado';


-- Crear la vista de envíos con información del cliente y estado
CREATE OR REPLACE VIEW vista_envios_clientes AS
SELECT e.id_envio, e.fecha_envio, e.fecha_estimada_entrega, e.direccion_destino, e.estado, 
       c.id_cliente, c.nombre, c.direccion, c.telefono, c.correo_electronico
FROM envios e
JOIN clientes c ON e.id_cliente = c.id_cliente;

-- Verificar la vista de envíos con información del cliente y estado
SELECT * FROM vista_envios_clientes;


-- Crear la vista de envíos entregados con tiempo total de envío

CREATE OR REPLACE VIEW vista_envios_entregados AS
SELECT e.id_envio, e.fecha_envio, e.fecha_estimada_entrega, 
       (e.fecha_estimada_entrega - e.fecha_envio) AS tiempo_total_envio,
       c.id_cliente, c.nombre
FROM envios e
JOIN clientes c ON e.id_cliente = c.id_cliente
WHERE e.estado = 'entregado';


-- Verificar la vista de envíos entregados con tiempo total de envío
SELECT * FROM vista_envios_entregados;

----prueba-------------------

-- Insertar el trigger
INSERT INTO envios (fecha_envio, fecha_estimada_entrega, direccion_destino, estado, id_cliente)
VALUES ('2024-06-10', '2024-06-10', 'santa anita', 'entregado', 2);

-- Verificar que el trigger haya registrado la inserción
SELECT * FROM registro_envios;



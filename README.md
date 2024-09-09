En este proyecto se trabajo con un archivo de base sobre el cual se reflejo en codigo un modelo de clases y se lo persistio en una base de datos H2.
Para hacer las relaciones se usaron las etiquetas OneToOne, OneToMany, ManyToOne y ManyToMany; ademas de etiquetas como @Entity, @Table, @Serial, @Column y @JoinColumn.
En mi caso no hice uso de Lombok por lo que los getters, setters y constructores estan explicitos en el codigo.

A continuacion se da una explicacion de algunas lineas importantes de nuestra clase principal:

- package Main;:Esta línea especifica que la clase PersistenceAppestá en el Mainpaquete.
- import Entidades.*;: Esta línea importa todas las clases del Entidadespaquete. Estas clases representan las entidades en la base de datos (por ejemplo, Factura, Domicilio, Cliente, Categoria, Articulo, DetalleFactura).
- EntityManagerFactory emf = Persistence.createEntityManagerFactory("example-unit");:Esta línea crea un EntityManagerFactory, que es una fábrica para crear EntityManagerinstancias. El Persistence.createEntityManagerFactory("example-unit")método busca una unidad de persistencia con el nombre "example-unit" en el persistence.xmlarchivo.
- EntityManager em = emf.createEntityManager();:Esta línea crea una EntityManagerinstancia, que se utiliza para interactuar con la base de datos.
- em.getTransaction().begin();:Esta línea inicia una nueva transacción. Las transacciones se utilizan para agrupar una serie de operaciones de base de datos que deben tratarse como una sola unidad de trabajo.
- El resto del código crea nuevas instancias de las entidades, establece sus propiedades y las agrega a la base de datos mediante el método EntityManager's persist.
- em.flush();:Esta línea vacía los EntityManagercambios de la base de datos.
- em.getTransaction().commit();:Esta línea confirma la transacción, lo que significa que todos los cambios realizados durante la transacción se guardarán permanentemente en la base de datos.
- em.getTransaction().rollback();:Esta línea revierte la transacción, lo que significa que se desharán todos los cambios realizados durante la transacción. Esto se utiliza en el catchbloque para gestionar cualquier excepción que pueda ocurrir durante la transacción.
- em.close();y emf.close();: Estas líneas cierran las instancias EntityManagery EntityManagerFactory, lo que libera cualquier recurso que estuvieran usando.

Trabajo realizado por Alvaro Ariza

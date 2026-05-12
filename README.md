from abc import ABC, abstractmethod
from datetime import datetime
import logging

# CONFIGURACIÓN DE LOGS

logging.basicConfig(
    filename="software_fj.log",
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)
# excepciones personalizadas
class clienteerror(excepcion):
   pass
class servicioerror(excepcion):
  pass
class reservaerror(excepcion):
   pass
# clase abstracta 

class entidadsistema(ABC):
abstractmethod 
def mostrainformacion (self):
   pass
# clase para cliente 

class cliente(entidadsistema):

def _init_(self, nombre, correo, telefono):
self.nombre=nombre 
self.correo=correo 
self.telefono=telefono 

self.validar_info()
#proceso de encapsulamiento
property
def nombre (self):
   return self.nombre 

property
def correo (self):
   return self.correo 

property 
def telefono(self):
   return self.telefono

def validar_datos(self):

  try:
       if len(self.nombre.strip()) < 3:
         raise clienteerror ("el nombre es demasiado corto")

       if "@" no in self.correo :
          raise clienteerror("ccorreo invalido ")
        if not self.telefono.isdigit():
          raise clienteerror ("el telefono debe contar con solo numero ")
 except clienteerror as e:
    logging.error(f"error validando cliente:{e}")
    raise 

def mostrar_informacion(self):
  return f"cliente: {self.nombre} | correo:{self.correo}"

#clase abstracta para servico

class servico(ABC)
    def _init_ (self, nombre, precio):
          self.nombre=nombre 
          self.precio=precio

    abstractmethod
    def calcular(self):
    pass

    abstractmethod
    def descripcion(self):
    pass

" servicio de reservas para salas

class reservasala(servicio):
     def _init_(self, nombre, precio, horas):
          super()._init_(nombre, precio)
          self.hroas=horas 

     def calcular(self, impuesto=0):
        if self.horas <=0:
           raise servicioerror("las horas deben ser mayores a cero")

        costo=self.precio*self.horas
        return costo + costo*impuesto)

    def descripcion(self):
       return f"reserva de sala por {self.horas} horas

#servicio alquiler de equipos 

class alquilerequipos(servico)

   def _init_(self, nombre, precio, dias):
      super()._init_(self, precio )
      self.dias=dias

    def calcularcosto(self, descuento=0):
        if self.dias<=0:
            raise servicioerror ("los dias deben ser mayores a cero ") 
        costo=self,precio*self,dias
        return costo - descuento 

    def descripcion(self):
       return f"alquiler de equipo por {self.dias} dias "

#servicio de asesorias 

class asesoriaespecilizada(servicio):
   def _init_(self, nombre, nivel):
      super()._init_(nombre,precio)
      self.nivel=nivel

   def calcular_Costo(self):
        multiplicar={
        "basica": 1,
        "media": 1,5,
        "avanzada": 2
        }

        if self.nivel not in multipplicador:
          raise servicioerror ("nivel de asesoria invalido ") 

        return self.precio * multiplicador [self.nivel]
    def descripcion(self):
       return f"asesoria especializada nivel {self.nivel}"

#clase para reserva 

class reserva:
  def _init_(self, cliente, servicio, duracion):

     if not isinstance(cliente, cliente):
         raise reservaerrror("cliente invalido")

     if not isinstance (servicio, servicio):
        raise reservaerror ("servicio invalido")

    self.cliente=cliente
    self.servicio=servicio
    self.duracion=duracion
    self.estado="pendiente"

def confirmar (self):

    try :
       self.estado ="confirmada"
       print("reserva confirmada")

    except excepcion as e:
         logging.error(f"error confirmando reserva:{e}")

def cancelar (self):

    try:
       self.estad="cancelada "
       print("reserva cancelada")

    finally:
        print("proceso de cancelacion finalizado ")

def proceso_reserva(self):

    try:
       costo= self.servicio. calcular_costo()
    except typeerror:
       costo=self.servicio.calcular_costo(0)

    except exception as e:
        logging.error(f"error procesado reserva:{e}")
        raise reservaerror("no fue posible procesar la reserva") from e

    else:
        print("reserva procesada correctamente")
        return costo

#listas internas 

clientes = []
servicios = []
reservas = []

#simulacion de operaciones

print ("\n=======SOFTWARE FJ =======\n")
#tipos de servicios validos e invalidos para el codigo 
operaciones = [

    #clientes validos 
    ("cliente", ("juan ruiz", "juan@gmail.com", "3203002340")),
    ("cliente", ("daira suarez", "dairasu@gmail.com", "3120008998")),

    #clientes invalidos
    ("cliente", ("jo", "correo-mal", "adc321")),
    ("cliente", ("david", "david@gmail.co", "telefono ")),

    #servicios validos 
    ("servicio_sala", ("sala premium", 60000, 3)),
    ("servicio_equipo", (proyector", 30000, 2)),
    ("servicio_asesoria", ("consultoria", 110000, "avanzada")),

    #servicios invalidos
    ("servicio_sala", ("sala error ", 40000, -1)),
    ("servicio_asesoria", ("asesoria error", 100000, "experto"))
    ]

    #proceso de codigo 

for operacion in operaciones:

    try:
       tipo = operacion[0]
       datos = operacion [1]

      if tipo == "cliente":
          cliente = cliente(*datos)
          clientes.append(cliente)

          print (f"cliente registrado: {cliente.nombre}")

     elif tipo == "servicio_sala":

           servicio= reservasala(*datos)
           servicios.append(servicio)

           print (servicio.descripcion())

     elif tipo =="servicio_equipo":

        servico == alquilerequipo(*datos)
        servicios.append(servicio)

        print (servicio.descripcion())

    elif tipo == "servicio_asesoria":

       servicio=asesoriaespecializada(*datos)
       servicios.append(servicio)

       print (servicio.descripcion())

except exception as e :
   print (F"error detectado:{e}")
   ligging.error(f"operacion fallida:{e}")



#creacion para reservas 

print("\n =======RESERVAS======\n")

try:

   reserva1 = reserva(clientes[0], servicios [0], 3)
   reservas.append(reserva1)

   reserva1.confirmar()

   costo = reserva1.procesar_reserva()

   print(f"costo total: ${costo]")

except exception as e:
   print (e)


try:

  reserva2 = reserva(clientes[1]. servicios [2]. 1)
  reservas.append(reserva2)

  reserva2.confirmar()

  costo = reserva2.procesar_reserva()

  print (f"costo total: ${costo}!)

except exception as e:
   print (e)


try:

#reserva invalida 
   reserva3 = reserva("cliente falso", servicios [1], 2)

except exception as e:
  print (f"error en la reserva: {e]")


try:

  reserva 4 = reserva(clientes[0], "servicio falso ", 2) 

except exception as e:
  print (f"error de reserva: {e}")
  logging.error(f"reserva invalida: {e}")



try:

  reserva5 = reserva(clientes[0], servicos[1], 2)

  reserva5.cancelar()

except exception as e:
  print(e) 


#resumen

print( "\n =====RESUMEN====")

print(f"clientes registrados: {len(clientes)}")
print(f" servicios registrados: {len(servicios)}")
print (f"reservas registrada:{len(reservas)}")

print("\nsistema ejecutando correctamente.")
print ("los errores fueron almacenados en software fj logs.txt")


      

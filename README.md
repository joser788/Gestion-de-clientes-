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

      

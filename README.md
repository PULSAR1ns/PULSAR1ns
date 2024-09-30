from datetime import datetime
import random

def patron_patente(patente_vehiculo):
  if len(patente_vehiculo) == 6:
    if patente_vehiculo[:2].isalpha() and patente_vehiculo[2:].isdigit():
        return True
    elif patente_vehiculo[:4].isalpha() and patente_vehiculo[4:].isdigit():
        return True
  return False

patentes_vehiculo = []
marcas_vehiculo = []
modelos_vehiculo = []
años_vehiculo = []
tipos_vehiculo = []
multas = []
fechas_registro = []
precios_vehiculo = []
cantidad_multas = []
nombres_dueño = []

while True :
  print ("#Bienvenido Automotora RUTA 40.")
  print("¿Que desea hacer hoy?")
  print ("1. Registrar vehículo")
  print ("2. Buscar información de vehiculo")
  print ("3. Impresión de Certificados")
  print ("4. Salir")

  try:
      opcion = int(input("Ingresa una opción (1-4): "))
      if opcion == 1:
          while True:
            patente_vehiculo = input("Ingresa la patente del vehiculo a registrar: (000.- Menú Principal) ").upper()
            if patente_vehiculo == '000':
                break
            if patron_patente(patente_vehiculo):
                print("Patente ingresada correctamente.- ")
                patentes_vehiculo.append(patente_vehiculo)
                break
            else:
                 print("Patente inválida! ")
                 print("Recuerda el formato AB1234 o ABCD12!")
          if patente_vehiculo == '000':
                continue


          while True:
            tipo_vehiculo = input("Ingresa el tipo de vehículo (AUTO-SUV-PICKUP-VAN): (000.- Menú Principal) ").upper()
            if tipo_vehiculo == '000':
                 break
            if tipo_vehiculo in ['AUTO', 'SUV', 'PICKUP', 'VAN']:
                 print("Tipo de vehículo ingresado correctamente.-")
                 tipos_vehiculo.append(tipo_vehiculo)
                 break
            else:
                 print("Tipo de vehiculo inválido! ")
                 print("Recuerda ingresar Auto, Suv, Pickup o Van para continuar!")
          if tipo_vehiculo == '000':
                 continue


          while True:
            marca_vehiculo = input("Ingresa la marca del vehiculo (2-12 caracteres): (000.- Menú Principal) ").upper()
            if marca_vehiculo == '000':
                 break
            if 2 <= len(marca_vehiculo) <= 12:
                 print("Marca ingresada correctamente.-")
                 marcas_vehiculo.append(marca_vehiculo)
                 break
            else:
                 print("Marca inválida! ")
                 print("Mínimo 2 caracteres y Maximo 12!")
          if marca_vehiculo == '000':
                 continue


          while True:
            modelo_vehiculo = input("Ingresa el modelo del vehículo: (000.- Menú Principal) ").upper()
            if modelo_vehiculo == '000':
                 break
            modelos_vehiculo.append(modelo_vehiculo)
            print("Modelo ingresado correctamente.-")
            break
          if modelo_vehiculo == '000':
                 continue


          while True:
            año_vehiculo = input("Ingresa el año del vehículo: (000.- Menú Principal)")
            if año_vehiculo == '000':
                 break
            if año_vehiculo.isdigit() and 1950 <= int(año_vehiculo) <= 2024:

                 print("Año ingresado correctamente.-")
                 años_vehiculo.append(año_vehiculo)
                 break
            else:
                 print("Año inválido! ")
                 print("Recuerda el año debe estar entre 1950 y 2024!")
          if año_vehiculo == '000':
             continue


          while True:
            precio_vehiculo = input("Ingresa el precio del vehiculo: (000.- Menú Principal) ")
            if precio_vehiculo == '000':
                 break
            if precio_vehiculo.isdigit() and int(precio_vehiculo) > 6880000:
                 print("Precio ingresado correctamente.-")
                 precios_vehiculo.append(int(precio_vehiculo))
                 break
            else:
                 print("Precio inválido! ")
                 print("Recuerda que el precio debe ser mayor a $6.880.000!")
          if precio_vehiculo == '000':
                 continue


          while True:
             numero_multas = input("Ingresa el número de multas del vehículo(000.- Menú Principal) ")
             if numero_multas == '000':
                break
             elif numero_multas.isdigit():
                numero_multas = int(numero_multas)
                cantidad_multas.append(numero_multas)
                if numero_multas == 0:
                 print("Vehículo registrado sin multas.-")
                 multas.append([])
                 break
                elif numero_multas > 0:
                 multas_vehiculo = []
                 for i in range(numero_multas):
                  print(f"Registro de multa numero {i + 1}/{numero_multas}. *Cada multa se debe registrar por separado*")


                  while True:
                      monto_multa = input(f"Ingresa el monto de la multa {i + 1}: (000.- Menú Principal) ")
                      if monto_multa == '000':
                        break
                      if monto_multa.isdigit():
                        monto_multa = int(monto_multa)

                        while True:
                            fecha_multa = input(f"Ingresa la fecha de la multa numero {i + 1} (dd/mm/aaaa) (000.- Menú Principal): ")
                            if fecha_multa == '000':
                                break
                            try:
                                formato_fecha = datetime.strptime(fecha_multa, '%d/%m/%Y')
                                print("Fecha ingresada correctamente.")
                                multas_vehiculo.append((monto_multa, fecha_multa))
                                break
                            except ValueError:
                                print("Fecha inválida! Recuerda el formato dd/mm/aaaa.")
                        break
                      else:
                        print("Monto inválido, por favor utiliza numeros.")
                if monto_multa == '000' or fecha_multa == '000':
                    break

                multas.append(multas_vehiculo)
                print("Multas registradas con éxito.")
                break
             else:
               print("Número de multas inválido. Debe ser un número entero.")


          while True:
            nombre_dueño = input("Ingresa el nombre del dueño del vehículo: (000.- Menú Principal)")
            if nombre_dueño == '000':
                 break
            print("Nombre ingresado correctamente.-")
            nombres_dueño.append(nombre_dueño)
            break
          if nombre_dueño == '000':
                 continue

          while True:
            fecha_registro = input("Ingresa la fecha en que se registra el vehiculo (dd/mm/aaaa) (000.- Menú Principal):")
            if fecha_registro == '000':
                 break
            try:
              formato_fecha = datetime.strptime(fecha_registro, '%d/%m/%Y')
              print("Fecha ingresada correctamente.-")
              print("Vehiculo registrado correctamente en el sistema.-!")
              fechas_registro.append(fecha_registro)
              break
            except ValueError:
                 print("Fecha invalida! ")
                 print("Recuerda el formato dd/mm/aaaa!")


      elif opcion == 2:
           while True:
            buscar_vehiculo = input("Ingresa la patente del vehículo que desea buscar: (000.- Menú Principal)").upper()
            if buscar_vehiculo == '000':
                break
            if buscar_vehiculo in patentes_vehiculo:
                    indice = patentes_vehiculo.index(buscar_vehiculo)
                    print()
                    print("Información del vehículo:")
                    print("Patente: " + patentes_vehiculo[indice])
                    print("Tipo: " + tipos_vehiculo[indice])
                    print("Marca: " + marcas_vehiculo[indice])
                    print("Modelo: " + modelos_vehiculo[indice])
                    print("Año: " + años_vehiculo[indice])
                    print("Precio: $" + str(precios_vehiculo[indice]))
                    print("Cantidad de multas: " + str(cantidad_multas[indice]))
                    print("Dueño: " + nombres_dueño[indice])
                    print("Fecha de registro del vehículo: " + fechas_registro[indice])
                    print()
                    break
            else:
                    print("Vehículo no encontrado, para consultar debe haber sido registrado anteriorimente!")
                    print("Recuerda el formato de patente AB1234 o ABCD12!")
                    break


      elif opcion == 3:
            print("Bienvenido a impresión de certificados")
            while True:
              patente_certificado = input("Ingresa la patente del vehículo para imprimir sus certificados: (000.- Menú Principal) ").upper()
              if patente_certificado == '000':
                break
              if patente_certificado in patentes_vehiculo:
                indice = patentes_vehiculo.index(patente_certificado)
                print("Patente valida.-")
                print("¿Que certificado desea imprimir?(1-3) (000.- Menú Principal)")
                print("1. Certificado de emisión de contaminantes")
                print("2. Certificado de anotaciones vigentes")
                tipo_certificado = input("3. Certificado de multas")
                if tipo_certificado == '000':
                  break

                if tipo_certificado == '1':
                    print("Certificado impreso correctamente.-")
                    print()
                    print("""###CERTIFICADO DE EMISIÓN DE CONTAMINANTES###""")
                    print("Dueño:" + nombres_dueño[indice])
                    print("Patente: " + patentes_vehiculo[indice])
                    print("Año fabricación: " + años_vehiculo[indice])
                    print("Certificado Valido.-")
                    print("Valor: $" + str(random.randint(2300, 5400)))
                    break

                elif tipo_certificado == '2':
                    print("Certificado impreso correctamente.-")
                    print()
                    print("""#CERTIFICADO DE ANOTACIONES VIGENTES#""")
                    print("Dueño:" + nombres_dueño[indice])
                    print("Patente: " + patentes_vehiculo[indice])
                    print("Año fabricación: " + años_vehiculo[indice])
                    print("Certificado Valido.-")
                    print("Valor: $" + str(random.randint(2300, 5400)))
                    break

                elif tipo_certificado == '3':
                    print("Certificado impreso correctamente.-")
                    print()
                    print("""#CERTIFICADO DE MULTAS#""")
                    print("Dueño:" + nombres_dueño[indice])
                    print("Patente: " + patentes_vehiculo[indice])
                    print("Multas: ")
                    multas_vehiculo = multas[indice]
                    for monto, fecha in multas[indice]:
                      print(f"Fecha: {fecha} - Monto: ${monto}")
                    print("Certificado Valido.-")
                    print("#Valor: $" + str(random.randint(2300, 5400)))
                    break

                else:
                    print("Opción inválida!")
                    print("(1-3 Seleccionar certificado) o (000.- Menú Principal)")

              else:
                print("Patente invalida! ")
                print("Recuerda que debe estar en el sistema para imprimir certificados")
                print("Recuerda el formato AB1234 o ABCD12!")
                break

      elif opcion == 4:
            print("¡Hasta luego! gracias por utilizar A40 Software V.1.0.0. ")
            print("Lucas Sánchez Olivos.-")
            break
      else:
            print("Opción no válida. Por favor, elige una opción del 1 al 4.")
  except ValueError:
        print("Entrada inválida. Por favor ingresa un número del 1 al 4.")

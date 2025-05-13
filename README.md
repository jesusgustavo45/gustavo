class Contabilidad:
    def __init__(self):
        self.transacciones = []

    def agregar_transaccion(self, tipo, descripcion, monto):
        if tipo.lower() not in ['ingreso', 'egreso']:
            print("Tipo inválido. Use 'ingreso' o 'egreso'.")
            return
        self.transacciones.append({
            'tipo': tipo.lower(),
            'descripcion': descripcion,
            'monto': monto
        })

    def mostrar_balance(self):
        ingresos = sum(t['monto'] for t in self.transacciones if t['tipo'] == 'ingreso')
        egresos = sum(t['monto'] for t in self.transacciones if t['tipo'] == 'egreso')
        saldo = ingresos - egresos
        print(f"\nBalance General")
        print(f"Ingresos: ${ingresos}")
        print(f"Egresos:  ${egresos}")
        print(f"Saldo:    ${saldo}")

    def mostrar_transacciones(self):
        print("\nTransacciones registradas:")
        for t in self.transacciones:
            print(f"{t['tipo'].capitalize()}: {t['descripcion']} - ${t['monto']}")


# Ejemplo de uso
libro = Contabilidad()
libro.agregar_transaccion('ingreso', 'Venta de productos', 1500)
libro.agregar_transaccion('egreso', 'Compra de materia prima', 500)
libro.agregar_transaccion('egreso', 'Pago de servicios', 200)

libro.mostrar_transacciones()
libro.mostrar_balance()

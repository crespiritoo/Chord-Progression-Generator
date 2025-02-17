import random
import tkinter as tk
from tkinter import ttk, messagebox


class GeneradorProgresiones:
    def __init__(self):
        # Definición de notas musicales
        self.notas = ['C', 'C#', 'D', 'D#', 'E', 'F', 'F#', 'G', 'G#', 'A', 'A#', 'B']

        # Diccionario expandido de progresiones por género
        self.progresiones_por_genero = {
            'rock': [
                ['I', 'IV', 'V', 'V'],
                ['I', 'V', 'vi', 'IV'],
                ['I', 'III', 'IV', 'iv'],
                ['i', 'III', 'VII', 'i'],
                ['I', 'V', 'IV', 'V'],
                ['I', 'bVII', 'iii', 'I']
            ],
            'pop': [
                ['I', 'V', 'vi', 'IV'],
                ['I', 'IV', 'V', 'V'],
                ['i', 'VI', 'III', 'VII'],
                ['I', 'bVII', 'IV', 'I'],
                ['i', 'v', 'VI', 'V']
            ],
            'jazz': [
                ['ii7', 'V7', 'Imaj7', 'Imaj7'],
                ['ii7', 'V7', 'Imaj7', 'vi7'],
                ['iiø7', 'V7b9', 'i7', 'VI7'],
                ['Imaj7', 'vi7', 'ii7', 'V7'],
                ['iii7', 'VI7', 'ii7', 'V7']
            ],
            'blues': [
                ['I7', 'I7', 'I7', 'I7', 'IV7', 'IV7', 'I7', 'I7', 'V7', 'IV7', 'I7', 'V7'],
                ['I7', 'IV7', 'I7', 'I7', 'IV7', 'IV7', 'I7', 'I7', 'V7', 'V7', 'I7', 'I7']
            ],
            'country': [
                ['I', 'IV', 'I', 'V'],
                ['I', 'V', 'IV', 'I'],
                ['vi', 'IV', 'I', 'V'],
                ['I', 'IV', 'vi', 'V']
            ],
            'clasica': [
                ['I', 'IV', 'V', 'I'],
                ['I', 'vi', 'IV', 'V'],
                ['I', 'V6', 'I', 'V'],
                ['vi', 'ii', 'V', 'I']
            ],
            'reggae': [
                ['I', 'V', 'vi', 'IV'],
                ['I7', 'IV7', 'I7', 'V7'],
                ['im', 'bVII', 'bVI', 'V'],
                ['i', 'bVII', 'bVI', 'bVII']
            ],
            'soul': [
                ['I7', 'IV7', 'V7', 'IV7'],
                ['ii7', 'V7', 'I7', 'vi7'],
                ['I7', 'iii7', 'vi7', 'IV7'],
                ['Imaj7', 'vi7', 'ii7', 'V7']
            ],
            'bossa_nova': [
                ['Imaj7', 'ii7', 'V7', 'Imaj7'],
                ['ii7b5', 'V7b9', 'im7', 'VI7'],
                ['Imaj7', 'IVmaj7', 'iiim7', 'VI7'],
                ['im7', 'IV7', 'iiim7b5', 'V7b9'],
                ['Imaj7', 'V7sus4', 'V7', 'Imaj7']
            ],
            'grunge': [
                ['I', 'IV', 'III', 'VI'],
                ['i', 'VII', 'IV', 'i'],
                ['I', 'bVI', 'bIII', 'bVII'],
                ['i', 'bVI', 'bIII', 'bVII']
            ]
        }

        # Diccionario expandido de acordes por modo
        self.acordes_por_modo = {
            'mayor': {
                'I': '', 'ii': 'm', 'iii': 'm', 'IV': '', 'V': '', 'vi': 'm', 'vii': 'dim',
                'I7': '7', 'ii7': 'm7', 'iii7': 'm7', 'IV7': '7', 'V7': '7', 'vi7': 'm7', 'vii7': 'm7b5',
                'Imaj7': 'maj7', 'V6': '6'
            },
            'menor': {
                'i': 'm', 'ii': 'dim', 'III': '', 'iv': 'm', 'v': 'm', 'VI': '', 'VII': '',
                'i7': 'm7', 'ii7': 'm7b5', 'III7': '7', 'iv7': 'm7', 'v7': 'm7', 'VI7': '7', 'VII7': '7',
                'iiø7': 'm7b5', 'V7b9': '7b9'
            }
        }

    def obtener_acorde(self, nota_base, grado, modo):
        # Obtener el índice de la nota base
        indice_base = self.notas.index(nota_base)

        # Mapeo expandido de grados a intervalos
        intervalos = {
            'I': 0, 'ii': 2, 'iii': 4, 'IV': 5, 'V': 7, 'vi': 9, 'vii': 11,
            'i': 0, 'II': 2, 'III': 4, 'iv': 5, 'v': 7, 'VI': 9, 'VII': 11,
            'bIII': 3, 'bVI': 8, 'bVII': 10,
            'I7': 0, 'ii7': 2, 'iii7': 4, 'IV7': 5, 'V7': 7, 'vi7': 9, 'vii7': 11,
            'Imaj7': 0, 'iiø7': 2, 'V7b9': 7
        }

        # Eliminar números y modificadores para obtener el grado base
        grado_base = ''.join(c for c in grado if c.isalpha() or c == 'b')

        # Calcular la nota del acorde
        intervalo = intervalos.get(grado_base, 0)
        indice_nota = (indice_base + intervalo) % 12
        nota = self.notas[indice_nota]

        # Agregar la calidad del acorde
        calidad = self.acordes_por_modo[modo].get(grado, '')

        return nota + calidad

    def generar_progresion(self, tonalidad, modo, genero, compas):
        if genero not in self.progresiones_por_genero:
            return "Género no soportado"

        progresion_base = random.choice(self.progresiones_por_genero[genero])
        acordes = [self.obtener_acorde(tonalidad, grado, modo) for grado in progresion_base]

        compases = int(compas.split('/')[0])
        acordes_por_compas = max(1, len(acordes) // compases)

        progresion_final = []
        for i in range(0, len(acordes), acordes_por_compas):
            compas_actual = acordes[i:i + acordes_por_compas]
            progresion_final.append(' - '.join(compas_actual))

        return progresion_final


class InterfazGrafica:
    def __init__(self):
        self.generador = GeneradorProgresiones()
        self.ventana = tk.Tk()
        self.ventana.title("Generador de Progresiones de Acordes")
        self.ventana.geometry("600x400")

        # Estilo
        self.ventana.configure(bg='#f0f0f0')
        style = ttk.Style()
        style.configure('TLabel', background='#f0f0f0', font=('Arial', 10))
        style.configure('TButton', font=('Arial', 10))
        style.configure('TCombobox', font=('Arial', 10))

        # Frame principal
        main_frame = ttk.Frame(self.ventana, padding="20")
        main_frame.grid(row=0, column=0, sticky=(tk.W, tk.E, tk.N, tk.S))

        # Tonalidad
        ttk.Label(main_frame, text="Tonalidad:").grid(row=0, column=0, pady=5)
        self.tonalidad = ttk.Combobox(main_frame, values=self.generador.notas, width=10)
        self.tonalidad.grid(row=0, column=1, pady=5)
        self.tonalidad.set('C')

        # Modo
        ttk.Label(main_frame, text="Modo:").grid(row=1, column=0, pady=5)
        self.modo = ttk.Combobox(main_frame, values=['mayor', 'menor'], width=10)
        self.modo.grid(row=1, column=1, pady=5)
        self.modo.set('mayor')

        # Género
        ttk.Label(main_frame, text="Género:").grid(row=2, column=0, pady=5)
        self.genero = ttk.Combobox(main_frame, values=list(self.generador.progresiones_por_genero.keys()), width=10)
        self.genero.grid(row=2, column=1, pady=5)
        self.genero.set('pop')

        # Compás
        ttk.Label(main_frame, text="Compás:").grid(row=3, column=0, pady=5)
        self.compas = ttk.Combobox(main_frame, values=['4/4', '3/4', '6/8'], width=10)
        self.compas.grid(row=3, column=1, pady=5)
        self.compas.set('4/4')

        # Botón generar
        ttk.Button(main_frame, text="Generar Progresión", command=self.generar).grid(row=4, column=0, columnspan=2,
                                                                                     pady=20)

        # Área de resultados
        self.resultado = tk.Text(main_frame, height=10, width=50)
        self.resultado.grid(row=5, column=0, columnspan=2, pady=10)

    def generar(self):
        try:
            progresion = self.generador.generar_progresion(
                self.tonalidad.get(),
                self.modo.get(),
                self.genero.get(),
                self.compas.get()
            )

            self.resultado.delete(1.0, tk.END)
            self.resultado.insert(tk.END, "Progresión generada:\n")
            self.resultado.insert(tk.END, "-" * 40 + "\n")
            for i, compas in enumerate(progresion, 1):
                self.resultado.insert(tk.END, f"Compás {i}: {compas}\n")

        except Exception as e:
            messagebox.showerror("Error", str(e))

    def iniciar(self):
        self.ventana.mainloop()


def main():
    app = InterfazGrafica()
    app.iniciar()


if __name__ == "__main__":
    main()

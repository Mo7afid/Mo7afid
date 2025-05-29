- 👋 Hi,from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.lang import Builder

kv = '''
<CalculatorLayout>:
    orientation: 'vertical'
    padding: 10
    spacing: 10

    TextInput:
        id: result
        font_size: 40
        size_hint_y: 0.2
        multiline: False
        readonly: True

    GridLayout:
        cols: 4
        spacing: 10
        size_hint_y: 0.8

        Button:
            text: "C"
            on_press: root.clear()
        Button:
            text: "⌫"
            on_press: root.delete()
        Button:
            text: "%"
            on_press: root.button_press("%")
        Button:
            text: "/"
            on_press: root.button_press("/")

        Button:
            text: "7"
            on_press: root.button_press("7")
        Button:
            text: "8"
            on_press: root.button_press("8")
        Button:
            text: "9"
            on_press: root.button_press("9")
        Button:
            text: "*"
            on_press: root.button_press("*")

        Button:
            text: "4"
            on_press: root.button_press("4")
        Button:
            text: "5"
            on_press: root.button_press("5")
        Button:
            text: "6"
            on_press: root.button_press("6")
        Button:
            text: "-"
            on_press: root.button_press("-")

        Button:
            text: "1"
            on_press: root.button_press("1")
        Button:
            text: "2"
            on_press: root.button_press("2")
        Button:
            text: "3"
            on_press: root.button_press("3")
        Button:
            text: "+"
            on_press: root.button_press("+")

        Button:
            text: "0"
            on_press: root.button_press("0")
        Button:
            text: "."
            on_press: root.button_press(".")
        Button:
            text: "="
            on_press: root.calculate()
'''

class CalculatorLayout(BoxLayout):
    def calculate(self):
        try:
            self.ids.result.text = str(eval(self.ids.result.text))
        except:
            self.ids.result.text = "خطأ"

    def clear(self):
        self.ids.result.text = ""

    def delete(self):
        self.ids.result.text = self.ids.result.text[:-1]

    def button_press(self, button):
        self.ids.result.text += str(button)

class CalculatorApp(App):
    def build(self):
        Builder.load_string(kv)
        return CalculatorLayout()

if __name__ == "__main__":
    CalculatorApp().run() 

<!---
Mo7afid/Mo7afid is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

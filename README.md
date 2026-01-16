from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.label import Label
from kivy.uix.button import Button
import time
import os

class MyApp(App):
    def build(self):
        layout = BoxLayout(orientation="vertical", padding=20, spacing=10)

        self.label = Label(text="My First APK", font_size=24)
        layout.add_widget(self.label)

        btn1 = Button(text="Show Directory")
        btn1.bind(on_press=self.show_dir)

        btn2 = Button(text="Show Time")
        btn2.bind(on_press=self.show_time)

        btn3 = Button(text="Exit")
        btn3.bind(on_press=lambda x: self.stop())

        layout.add_widget(btn1)
        layout.add_widget(btn2)
        layout.add_widget(btn3)

        return layout

    def show_dir(self, instance):
        self.label.text = os.getcwd()

    def show_time(self, instance):
        self.label.text = time.ctime()

MyApp().run()

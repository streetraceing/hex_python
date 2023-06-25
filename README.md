## Генерация линейных градиентов для майнкрафта
 Простой код, создающий градиенты, используемые в Minecraft.

 Пример вывода кода:
 > &#ff0000H&#e8170ce&#d12e18l&#b94624l&#a25d30o&#8b743c &#748b48W&#5da254o&#46b960r&#2ed16cl&#17e878d&#00ff84!

 ![Картинка не была загружена :(](https://i.imgur.com/U5suFDv.png "Вывод")
 

``` python
import matplotlib as mpl
import numpy as np

def interpolate(c1,c2,mix=0): # Функция считающая линейную интерполяцию
    c1=np.array(mpl.colors.to_rgb(c1))
    c2=np.array(mpl.colors.to_rgb(c2))
    return mpl.colors.to_hex((1-mix)*c1 + mix*c2)

def buildGradient(color1:str,color2:str,text:str): # Постройка массива с градиентом 
    result = []
    n = len(text)-1
    for x in range(n+1):
        result.append(interpolate(color1,color2,x/n))
    return result

def buildString(gradients, text:str): # Объединение введенных символов и градиента
    result = []
    for i in range(len(text)):
        result.append(f'&{gradients[i]}{text[i]}')
    return result

def createGradient(color1, color2, text): # Объединяем функции, для удобности кода
    gradients = buildGradient(color1, color2, text)
    result = buildString(gradients, text)
    return ''.join(result)

# тестовый запуск
if __name__ == "__main__":
    print(createGradient("#FFFFFF","#000000","12345"))
```

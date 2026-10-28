
Your phone shows its battery as a row of **5 bars**. Each full bar represents 20% of charge. A bar only lights up when its whole 20% is reached.

Write a function `battery_bars(percent)` that returns the battery as a string: `#` for a lit bar, `.` for an empty one, all wrapped in square brackets.

```python
battery_bars(100)  # => "[#####]"
battery_bars(70)   # => "[###..]"
battery_bars(20)   # => "[#....]"
battery_bars(19)   # => "[.....]"
battery_bars(0)    # => "[.....]
```

**Solución:**
```Java
import java.util.*;  
  
public class Kata {  
  
    public static String batteryBars(int percent) {  
        if (percent < 20 && percent >= 0) {  
            return "[.....]";  
        }else if (percent < 40 && percent >= 20) {  
            return "[#....]";  
        }else if (percent < 60 && percent >= 40) {  
            return "[##...]";  
        }else if (percent < 80 && percent >= 60) {  
            return "[###..]";  
        }else if (percent < 100 && percent >= 80) {  
            return "[####.]";  
        }else if (percent == 100) {  
            return "[#####]";  
        }  
        return "";  
    }  
  
    public static void main(String[] args) {  
        var sc = new Scanner(System.in);  
        System.out.print("Ingrese el valor de su bateria: ");  
        var carga =  sc.nextInt();  
        System.out.println(batteryBars(carga));  
    }  
}
```

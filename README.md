# 📌 Condiciones y Validaciones en Java (NetBeans) 🚀
Forked del Notion de [David E.](https://ruby-lemongrass-2ac.notion.site/Condiciones-y-1904ff277c4880c3a6badc3c3d2089c4) 

## ✅ 1. Limitar el Número de Caracteres
```java
private void limitarCaracteresKeyTyped(java.awt.event.KeyEvent evt, int maxLength) {
    if (campoTexto.getText().length() >= maxLength) { 
        evt.consume();
    }
}
```
**Explicación:** Restringe la entrada a un máximo indicado en maxLength.

---

## ✅ 2. Permitir Solo Números
```java
private void soloNumerosKeyTyped(java.awt.event.KeyEvent evt) {
    char c = evt.getKeyChar();
    if (!Character.isDigit(c)) { // Solo permite dígitos
        evt.consume();
    }
}
```
**Explicación:** Permite solo números del 0 al 9.

---

## ✅ 3. Permitir Solo Letras
```java
private void soloLetrasKeyTyped(java.awt.event.KeyEvent evt) {
    char c = evt.getKeyChar();
    if (!Character.isLetter(c) && !Character.isWhitespace(c)) { // Letras y espacios
        evt.consume();
    }
}
```
**Explicación:** Restringe la entrada a letras y espacios.

---

## ✅ 4. Validar Formato de DNI (8 Dígitos + 1 Letra)
```java
private void validarDNIKeyTyped(java.awt.event.KeyEvent evt) {
    char c = evt.getKeyChar();
    String texto = campoDNI.getText();

    if (texto.length() < 8) {
        if (!Character.isDigit(c)) {
            evt.consume();
        }
    } else if (texto.length() == 8) {
        if (!Character.isLetter(c)) {
            evt.consume();
        }
    } else {
        evt.consume();
    }
}
```
**Explicación:** Permite ingresar un DNI válido con 8 números seguidos de una letra.

---

## ✅ 5. Validar Teléfono (9 Dígitos Máximo)
```java
private void validarTelefonoKeyTyped(java.awt.event.KeyEvent evt) {
    char c = evt.getKeyChar();
    if (!Character.isDigit(c) || campoTelefono.getText().length() >= 9) {
        evt.consume();
    }
}
```
**Explicación:** Limita el número de teléfono a 9 dígitos.

---

## ✅ 6. Validar Email
```java
private boolean validarEmail(String email) {
    return email.matches("^[A-Za-z0-9+_.-]+@[A-Za-z0-9.-]+$");
}
```
**Explicación:** Verifica que el texto tenga un formato válido de correo electrónico.

---

## ✅ 7. Validar Longitud Mínima y Máxima
```java
private void validarLongitudKeyTyped(java.awt.event.KeyEvent evt) {
    int min = 5;
    int max = 15;

    if (campoTexto.getText().length() >= max) {
        evt.consume();
    }
}
```
**Explicación:** Controla que el texto tenga entre 5 y 15 caracteres.

---

## ✅ 8. Validar Números Decimales
```java
private void validarDecimalKeyTyped(java.awt.event.KeyEvent evt) {
    char c = evt.getKeyChar();
    String texto = campoDecimal.getText();

    if (!Character.isDigit(c) && c != '.') {
        evt.consume();
    }
    if (c == '.' && texto.contains(".")) {
        evt.consume();
    }
}
```
**Explicación:** Permite ingresar números decimales con un solo punto.

---

## ✅ 9. Validar Solo Texto Alfabético (Sin Espacios)
```java
private void validarSoloTextoKeyTyped(java.awt.event.KeyEvent evt) {
    char c = evt.getKeyChar();
    if (!Character.isLetter(c)) {
        evt.consume();
    }
}
```
**Explicación:** Permite solo letras sin espacios.

---

## ✅ 10. Validar Campos Vacíos
```java
private boolean validarCampoVacio(String texto) {
    return texto.trim().isEmpty();
}
```
**Explicación:** Verifica si un campo de texto está vacío.

---

## ✅ 11. Validar Que No Haya Caracteres Especiales
```java
private void sinCaracteresEspecialesKeyTyped(java.awt.event.KeyEvent evt) {
    char c = evt.getKeyChar();
    if (!Character.isLetterOrDigit(c) && !Character.isWhitespace(c)) {
        evt.consume();
    }
}
```
**Explicación:** Restringe la entrada de caracteres especiales como `@`, `#`, `$`, etc.

---

## ✅ 12. Validar Que No Se Ingresen Espacios
```java
private void sinEspaciosKeyTyped(java.awt.event.KeyEvent evt) {
    if (Character.isWhitespace(evt.getKeyChar())) {
        evt.consume();
    }
}
```
**Explicación:** Restringe la entrada de espacios, útil para contraseñas o códigos.

---

## ✅ 13. Comparar Fechas con JSpinner
### Comparar dos fechas (introducidas en dos `JSpinner`)
```java
import java.util.Date;

private void compararFechasActionPerformed(java.awt.event.ActionEvent evt) {
    Date fecha1 = (Date) spinnerFecha1.getValue();
    Date fecha2 = (Date) spinnerFecha2.getValue();

    if (fecha1.before(fecha2)) {
        JOptionPane.showMessageDialog(this, "La Fecha 1 es anterior a la Fecha 2.");
    } else if (fecha1.after(fecha2)) {
        JOptionPane.showMessageDialog(this, "La Fecha 1 es posterior a la Fecha 2.");
    } else {
        JOptionPane.showMessageDialog(this, "Ambas fechas son iguales.");
    }
}
```
**Explicación:**
- `before()` verifica si `fecha1` es anterior a `fecha2`.
- `after()` verifica si `fecha1` es posterior a `fecha2`.
- Si ninguna de las condiciones se cumple, significa que son iguales.

---

## ✅ 14. Comparar una fecha ingresada con la fecha actual
```java
import java.util.Date;

private void compararConFechaActualActionPerformed(java.awt.event.ActionEvent evt) {
    Date fechaIngresada = (Date) spinnerFecha.getValue();
    Date fechaActual = new Date(); // Obtiene la fecha actual del sistema

    if (fechaIngresada.before(fechaActual)) {
        JOptionPane.showMessageDialog(this, "La fecha ingresada es anterior a hoy.");
    } else if (fechaIngresada.after(fechaActual)) {
        JOptionPane.showMessageDialog(this, "La fecha ingresada es posterior a hoy.");
    } else {
        JOptionPane.showMessageDialog(this, "La fecha ingresada es hoy.");
    }
}
```
**Explicación:**
- `new Date()` obtiene la fecha actual del sistema.
- Se compara la fecha ingresada con la fecha actual usando `before()` y `after()`.



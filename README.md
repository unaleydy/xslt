<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
<xsl:output method="html" indent="yes"/>
<xsl:template match="/">
<html>
<head>
<title>Tabla de Máquinas</title>
</head>
<body>
<h1>Tabla de Máquinas</h1>
<table border="1">
<tr>
<th>Máquina</th>
<th>Tipo</th>
<th>Procesador</th>
<th>Memoria</th>
</tr>
<xsl:apply-templates select="equipos/máquina"/>
</table>
</body>
</html>
</xsl:template>
<xsl:template match="equipos/máquina">
<tr>
<td>
<a href="{concat('http://',config/IP)}"><xsl:value-of select="@nombre"/></a>
</td>
<td> 
<xsl:if test="starts-with(hardware/tipo/text(),'impresora')">
<img src="img/impresora.png" height="46" width="40"/>
</xsl:if>
<xsl:if test="hardware/tipo/text()='PC sobremesa'">
<img src="img/sobremesa.png" height="46" width="40"/>
</xsl:if>
<xsl:if test="hardware/tipo/text()='Semitorre'">
<img src="img/semitorre.jpg" height="46" width="40"/>
</xsl:if>
<xsl:if test="hardware/tipo/text()='Torre'">
<img src="img/torre.jpg" height="46" width="40"/>
</xsl:if>
<xsl:if test="hardware/tipo/text()='Rack'">
<img src="img/rack.png" height="46" width="40"/>
</xsl:if>
</td>
<td><xsl:value-of select="hardware/procesador"/></td>
<td><xsl:value-of select="hardware/memoria"/>GB</td>
</tr>
</xsl:template>
</xsl:stylesheet>

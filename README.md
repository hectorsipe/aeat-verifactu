# VeriFactu AEAT - Esquemas y Servicios

Este repositorio contiene los archivos WSDL y XSD necesarios para implementar una integración técnica con la Agencia Tributaria (AEAT) en el marco del Sistema de Facturación VeriFactu, incluyendo:

- Remisión voluntaria de registros de facturación
- Consulta de registros emitidos
- Anulación y subsanación

## 🔧 Contenido

| Carpeta | Descripción |
|--------|-------------|
| `wsdl/` | WSDL oficial del servicio `SistemaFacturacion` |
| `xsd/`  | Archivos de esquema XML usados por el WSDL |
| `examples/` | Configuraciones de Maven para generar clases con JAX-WS |

## 🛠️ Generar clases Java (con Maven)

Puedes usar el siguiente plugin en tu `pom.xml`:

```xml
<plugin>
  <groupId>org.codehaus.mojo</groupId>
  <artifactId>jaxws-maven-plugin</artifactId>
  <version>2.6</version>
  <executions>
    <execution>
      <goals>
        <goal>wsimport</goal>
      </goals>
      <configuration>
        <wsdlDirectory>${project.basedir}/src/main/resources/wsdl</wsdlDirectory>
        <wsdlFiles>
          <wsdlFile>SistemaFacturacion.wsdl</wsdlFile>
        </wsdlFiles>
        <packageName>com.aeat.verifactu.ws</packageName>
        <sourceDestDir>${project.build.directory}/generated-sources/wsdl</sourceDestDir>
        <extension>true</extension>
        <verbose>true</verbose>
      </configuration>
    </execution>
  </executions>
</plugin>

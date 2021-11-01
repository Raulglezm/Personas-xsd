# Personas-xsd
![image](https://user-images.githubusercontent.com/91153605/139733483-e742ed34-46b3-4222-9471-5768919ed7c8.png)

## Código

```bash
<?xml version="1.0" encoding="ISO-8859-1"?>

<xsd:schema xmlns:xs="https://www.w3.org/2001/XMLSchema">

	<xs:element name = "personas">

		<xs:complexType>

			<xs:sequences>

				<xs:element ref = "nombre">
				<xs:element ref = "nacimiento" min0ccurs="0" max0ccurs="1"/>
				<xs:element ref = "dirección" min0ccurs="0" max0ccurs="unbounded"/>
				<xs:choice>

					<xs:element name="varon"/>
					<xs:element name="hembra"/>

				</xs:choice>
			</xs:sequences>
		</xs:complexType>
	</xs:element>

	<xs:simpleType name="tipoNombre">
		<xs:restriction base="xsd:string">
			<xs:minLength value = "0"/>
			<xs:maxlength value="50"/>
		</xs:restriction>
	</xs:simpleType>

	<xs:element name = "nombre" type = "tipoNombre"/>
	<xs:element name = "calle" type = "tipoNombre"/>
	<xs:element name = "poblacion" type = "tipoNombre"/>
	<xs:element name = "provincia" type = "tipoNombre"/>

	<xs:element name = "nacimiento">
		<xs:complexType>
			<xs:simpleContent>
				<xs:extension base="xs:string">
					<xs:attribute name ="dia" type="tipoDia"/>
					<xs:attribute name ="mes" type="tipoMes"/>
					<xs:attribute name ="Anyo" type="tipoAnyo"/>
				</xs:extension>
			</xs:simpleContent>
		</xs:complexType>
	</xs:element>

	<xs:simpleType name = "tipoDia">
		<xs:restriction base = "xsd:positiveInteger">
			<xs:minInclusive value = "1"/>
			<xs:maxInclusive value = "31"/>
		</xs:restriction>
	</xs:simpleType>

	<xs:simpleType name = "tipoMes">
		<xs:restriction base = "xs:string">
			<xs:ennumeration value = "Enero"/>
			<xs:ennumeration value = "Febrero"/>
			<xs:ennumeration value = "Marzo"/>
			<xs:ennumeration value = "Abril"/>
			<xs:ennumeration value = "Mayo"/>
			<xs:ennumeration value = "Junio"/>
			<xs:ennumeration value = "Julio"/>
			<xs:ennumeration value = "Agosto"/>
			<xs:ennumeration value = "Septiembre"/>
			<xs:ennumeration value = "Octubre"/>
			<xs:ennumeration value = "Noviembre"/>
			<xs:ennumeration value = "Diciembre"/>
		</xs:restriction>
	</xs:simpleType>

	<xs:simpleType name = "TipoAnyo">
		<xs:restriction base = "xsd:String">
			<xs:minLength value = "0"/>
			<xs:maxlength value = "50"/>
		</xs:restriction>
	</xs:simpleType>

	<xs:element name = "direccion">
		<xs:complexType>
			<xs:sequences>
				<xs:element ref = "calle"/>
				<xs:element ref = "poblacion"/>
				<xs:element ref = "provincia"/>
				<xs:element ref = "tipoCodPostal"/>
			</xs:sequences>
		</xs:complexType>
	</xs:element>

	<xs:complexType name = "tipoCodPostal">
		<xs:element name = "cpostal">
			<xs:restriction base = "xsd:positiveInteger">
				<xs:totalDigits value = "5"/>
			</xs:restriction>
		</xs:element>
	</xs:complexType>

</xs:schema>




<?xml version="1.0" encoding="ISO-8859-1" ?>

<personas>
	<persona>
		<nombre>Juan Pardo</nombre>
		
		<nacimiento dia = "10" mes = "Abril" anyo = "1982"/>
		<direccion>
			<calle>Caoba, 1</calle>
			<poblacion>Madrid</poblacion>
			<provincia>Madrid</provincia>
			<cpostal>28005</cpostal>
		</direccion>
	</persona>

	<persona>

		<nombre>María López</nombre>
		
		<direccion>
			<calle>Roncato, 1</calle>
			<poblacion>Illesca</poblacion>
			<provincia>Toledo</provincia>
			<cpostal>45200</cpostal>
		</direccion>
		<direccion>
			<calle>Paseo de la Esperanza, 15, 1ºA</calle>
			<poblacion>Madrid</poblacion>
			<provincia>Madrid</provincia>
			<cpostal>28005</cpostal>
		</direccion>
	</persona>
</personas>
```

## Proceso 

Tras apuntar las diferentes características y relacionarlas entre ellas para saber a qué corresponde cada una, empecé a formular el xsd, y analizando cuales de ellos era necesario hacer referencias o un llamamiento. Tras el primer paso empecé a crear las referencias con sus distintas cualidades y por último analicé cuales eran las restricciones necesarias y las definí.

---
title: Entrada de XmlDocument en XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: c7819c3cb6b1430dcdb8a78c43f7138f64e691a8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709847"
---
# <a name="xmldocument-input-to-xsltransform"></a>Entrada de XmlDocument en XslTransform
La clase <xref:System.Xml.XmlDocument> permite modificar un documento XML. Si el XML necesita editarse o modificarse antes de ser enviado al método <xref:System.Xml.Xsl.XslTransform.Transform%2A>, cargue el XML en <xref:System.Xml.XmlDocument>, edítelo y envíelo a <xref:System.Xml.Xsl.XslTransform>.  
  
> [!NOTE]
> La clase <xref:System.Xml.Xsl.XslTransform> está obsoleta en .NET Framework 2.0. Puede llevar a cabo Extensible Stylesheet Language for Transformations (XSLT) mediante la clase <xref:System.Xml.Xsl.XslCompiledTransform>. Consulte [Uso de la clase XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) y [Migración desde la clase XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) para obtener más información.  
  
 <xref:System.Xml.XmlDocument> implementa la interfaz <xref:System.Xml.XPath.IXPathNavigable>, de forma que el documento puede pasarse al método <xref:System.Xml.Xsl.XslTransform.Transform%2A> después de la edición.  
  
 Debido a la capacidad de edición de <xref:System.Xml.XmlDocument>, utilizar la clase <xref:System.Xml.XmlDocument> como entrada a una transformación es más lento que usar <xref:System.Xml.XPath.XPathDocument> para las transformaciones Extensible Stylesheet Language for Transformations (XSLT), ya que <xref:System.Xml.XPath.XPathDocument> se optimiza para las consultas XML Path Language (XPath) debido al almacenamiento interno.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código muestra cómo <xref:System.Xml.XmlDocument> puede suministrarse a <xref:System.Xml.Xsl.XslTransform>, con el resultado enviado a <xref:System.Xml.XmlReader>.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a>Vea también

- <xref:System.Xml.XmlDocument>
- [Transformaciones XSLT con la clase XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [La clase XslTransform implementa el procesador XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [XPathNavigator en transformaciones](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [XPathNodeIterator en transformaciones](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Entrada XPathDocument en XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Entrada de XmlDataDocument en XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)

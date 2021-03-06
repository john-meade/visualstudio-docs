---
title: "Late Binding in Office Solutions | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "objects [Office development in Visual Studio], casting"
  - "types [Office development in Visual Studio], casting"
  - "automation [Office development in Visual Studio], casting objects"
  - "casting, object to specific type"
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Late Binding in Office Solutions
  Some types in the object models of Office applications provide functionality that is available through late-binding features. For example, some methods and properties can return different types of objects depending on the context of the Office application, and some types can expose different methods or properties in different contexts.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic projects where **Option Strict** is off and Visual C# projects that target the [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] or the [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] can work directly with types that employ these late-binding features.  
  
## Implicit and Explicit Casting of Object Return Values  
 Many methods and properties in the Microsoft Office primary interop assemblies (PIAs) return <xref:System.Object> values, because they can return several different types of objects. For example, the <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> property returns an <xref:System.Object> because its return value can be a <xref:Microsoft.Office.Interop.Excel.Worksheet> or <xref:Microsoft.Office.Interop.Excel.Chart> object, depending on what the active sheet is.  
  
 When a method or property returns a <xref:System.Object>, you must explicitly convert (in Visual Basic) the object to the correct type in Visual Basic projects where **Option Strict** is on. You do not have to explicitly cast <xref:System.Object> return values in Visual Basic projects where **Option Strict** is off.  
  
 In most cases, the reference documentation lists the possible types of the return value for a member that returns an <xref:System.Object>. Converting or casting the object enables IntelliSense for the object in the Code Editor.  
  
 For information about conversion in Visual Basic, see [Implicit and Explicit Conversions &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) and [CType Function &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### Examples  
 The following code example demonstrates how to cast an object to a specific type in a Visual Basic project where **Option Strict** is on. In this type of project, you must explicitly cast the <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> property to a <xref:Microsoft.Office.Interop.Excel.Range>. This example requires a document-level Excel project with a worksheet class named `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 The following code example demonstrates how to implicitly cast an object to a specific type in a Visual Basic project where **Option Strict** is off or in a Visual C# project that targets the [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. In these types of projects, the <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> property is implicitly cast to a <xref:Microsoft.Office.Interop.Excel.Range>. This example requires a document-level Excel project with a worksheet class named `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-cs[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## Accessing Members That Are Available Only Through Late Binding  
 Some properties and methods in the Office PIAs are available only through late binding. In Visual Basic projects where **Option Strict** is off or in Visual C# projects that target the [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] or the [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], you can use the late binding features in these languages to access late-bound members. In Visual Basic projects where **Option Strict** is on, you must use reflection to access these members.  
  
### Examples  
 The following code example demonstrates how to access late-bound members in a Visual Basic project where **Option Strict** is off or in a Visual C# project that targets the [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. This example accesses the late-bound **Name** property of the **File Open** dialog box in Word. To use this example, run it from the `ThisDocument` or `ThisAddIn` class in a Word project.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-cs[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 The following code example demonstrates how to use reflection to accomplish the same task in a Visual Basic project where **Option Strict** is on.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## See Also  
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)   
 [Using Type dynamic &#40;C&#35; Programming Guide&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflection &#40;C&#35; and Visual Basic&#41;](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)   
 [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md)  
  
  
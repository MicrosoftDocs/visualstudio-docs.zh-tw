---
title: "使用 Automation 模型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 82a9c2068bdd3e234bcc53ffa870ca289289d690
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="using-the-automation-model"></a>使用 Automation 模型
VSPackage 連接自動化之後，您可以取得的屬性和方法的呼叫<xref:EnvDTE.DTEClass.GetObject%2A>方法<xref:EnvDTE._DTE>物件，傳遞字串，表示您想要擷取的物件。  
  
## <a name="obtaining-project-objects"></a>取得專案的物件  
 以下是兩個程式碼範例示範如何自動化取用者會包含專案 automation 物件。 如需如何取得 DTE 物件相關資訊，請參閱[How to： 取得參考的 DTE 和 DTE2 物件](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4)。  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 此時，您可以使用標準的專案物件屬於特定 VSPackage 也可以下移階層的模型。  
  
 下列程式碼範例示範如何取得自訂物件所自訂的專案類型的屬性。:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 下列程式碼列出所有中的屬性名稱[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境**一般**選項**工具**功能表：  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:EnvDTE.DTEClass.GetObject%2A>

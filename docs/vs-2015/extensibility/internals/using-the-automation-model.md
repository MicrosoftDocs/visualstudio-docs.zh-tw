---
title: 使用 Automation 模型 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51579a61cad76cd3164a8ddce739511e7a81d622
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203173"
---
# <a name="using-the-automation-model"></a>使用 Automation 模型
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您已經連接 VSPackage 自動化之後，您可以藉由呼叫取得的屬性和方法<xref:EnvDTE.DTEClass.GetObject%2A>方法<xref:EnvDTE._DTE>物件，並傳遞字串，表示您想要擷取的物件。  
  
## <a name="obtaining-project-objects"></a>取得專案物件  
 以下是兩個程式碼範例示範如何自動化取用者會取得專案 automation 物件。 如需有關如何取得 DTE 物件的資訊，請參閱 <<c0> [ 如何： 取得參考 DTE 和 DTE2 物件](http://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4)。  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 此時，您可以使用標準專案的物件屬於特定 VSPackage 也可以下移階層的模型。  
  
 下列程式碼範例示範如何取得自訂專案類型的屬性的自訂物件。:  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 下列程式碼會列出所有的屬性名稱[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]環境**一般**選項**工具**功能表：  
  
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


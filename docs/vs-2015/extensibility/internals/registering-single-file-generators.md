---
title: 註冊單一檔案產生器 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d500227f60552fea171b038523808e4409cf9c33
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498881"
---
# <a name="registering-single-file-generators"></a>註冊單一檔案產生器
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[註冊單一檔案產生器](https://docs.microsoft.com/visualstudio/extensibility/internals/registering-single-file-generators)。  
  
若要提供自訂的工具[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，您必須註冊因此[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]可以加以具現化，並與特定專案類型關聯。  
  
### <a name="to-register-a-custom-tool"></a>若要註冊自訂的工具  
  
1.  請註冊自訂的工具 DLL 中[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]本機登錄或在系統登錄中，HKEY_CLASSES_ROOT 之下。  
  
     例如，以下是受管理 MSDataSetGenerator 自訂工具，隨附的註冊資訊[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  建立以所需的登錄機碼[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]產生器下的 hive\\*GUID*位置*GUID*由特定語言的專案系統或服務所定義的 GUID。 索引鍵的名稱會變成您的自訂工具的程式設計名稱。 自訂工具的索引鍵具有下列值：  
  
    -   (預設值)  
  
         選擇性。 提供自訂工具的使用者易記描述。 這個參數是選擇性的但建議使用。  
  
    -   CLSID  
  
         必要。 指定識別碼的 COM 元件實作的類別庫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>。  
  
    -   GeneratesDesignTimeSource  
  
         必要。 指出是否從這個自訂的工具所產生的檔案類型都會提供給視覺化設計工具。 此參數的值必須是 （零） 針對至視覺化設計工具無法使用的類型為 0 或 （一） 1 類型可用來視覺化設計工具。  
  
    > [!NOTE]
    >  您必須註冊自訂的工具，分別為每個您想要自訂的工具，使其可用的語言。  
  
     比方說，MSDataSetGenerator 將本身註冊一次針對每種語言：  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)   
 [判斷專案的預設命名空間](../../misc/determining-the-default-namespace-of-a-project.md)   
 [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager 物件簡介](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)


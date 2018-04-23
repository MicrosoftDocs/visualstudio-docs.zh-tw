---
title: 註冊單一檔案產生器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9b7d16a9e473028d85540f4447d9981382be0fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="registering-single-file-generators"></a>註冊單一檔案產生器
若要啟用自訂的工具在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，必須註冊，因此[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可以具現化，並與特定專案類型關聯。  
  
### <a name="to-register-a-custom-tool"></a>若要註冊自訂的工具  
  
1.  請註冊自訂的工具 DLL 中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本機登錄或在系統登錄中，其內。  
  
     例如，以下是 managed MSDataSetGenerator 自訂工具，隨附於的註冊資訊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  建立所需的登錄機碼[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]產生器下的登錄區\\*GUID*其中*GUID* GUID 所定義的特定語言專案系統或服務。 索引鍵的名稱會變成您的自訂工具的程式設計名稱。 自訂工具的索引鍵具有下列值：  
  
    -   (預設值)  
  
         選擇性。 提供的自訂工具的使用者易記描述。 這個參數是選擇性的但建議使用。  
  
    -   CLSID  
  
         必要。 指定的類別庫實作的 COM 元件的識別碼<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>。  
  
    -   GeneratesDesignTimeSource  
  
         必要。 指出是否從這個自訂的工具所產生的檔案類型都會提供給視覺化設計工具。 此參數的值必須為類型不適用於視覺化設計工具 （零） 0 或 1 （一） 可以使用視覺化設計工具類型。  
  
    > [!NOTE]
    >  您必須註冊自訂的工具，分別為每個想要使用自訂工具的語言。  
  
     例如，MSDataSetGenerator 自行註冊一次針對每個語言：  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)   
 [若要公開的視覺化設計工具的類型](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager 物件簡介](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
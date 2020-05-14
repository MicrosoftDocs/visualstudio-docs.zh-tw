---
title: 註冊單個檔案產生器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705804"
---
# <a name="registering-single-file-generators"></a>註冊單一檔案產生器
要使自定義工具在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中 可用,必須註冊它[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)],以便 實例化它並將其與特定的項目類型關聯。

### <a name="to-register-a-custom-tool"></a>註冊自訂工具

1. 在HKEY_CLASSES_ROOT的情況下,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在本地註冊表或系統註冊表中註冊自訂工具 DLL。

    例如,下面是託管 MSDataSetGenerator 自訂工具的註冊資訊,該工具附[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]帶 :

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. 在\\生成器*GUID*下[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]所需的配置單元中創建註冊表項,其中*GUID*是由特定語言的專案系統或服務定義的 GUID。 密鑰的名稱將成為自定義工具的程式設計名稱。 自訂工具鍵具有以下值:

   - (預設值)

        選擇性。 提供自定義工具的使用者友好說明。 此參數是可選的,但建議使用。

   - CLSID

        必要。 指定實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>的 COM 元件的類庫的識別碼。

   - 產生設計時間來源

        必要。 指示此自定義工具生成的檔中的類型是否可供可視化設計器使用。 對於視覺設計器不可用的類型,此參數的值需要為 (零) 0,對於可視化設計器可用的類型,則需要 (1) 1。

   > [!NOTE]
   > 您必須為希望自定義工具可用的每種語言分別註冊自定義工具。

    例如,MSDataSet產生器為每個語言註冊一次:

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
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)
- [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [BuildManager 物件簡介](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)

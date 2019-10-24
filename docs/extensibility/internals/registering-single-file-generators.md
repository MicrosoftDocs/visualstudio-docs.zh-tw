---
title: 註冊單一檔案產生器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9026da08272d69bac246f98ae741a47527d627f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724557"
---
# <a name="registering-single-file-generators"></a>註冊單一檔案產生器
若要在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中提供自訂工具，您必須註冊它，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可以將它具現化，並將其與特定的專案類型產生關聯。

### <a name="to-register-a-custom-tool"></a>註冊自訂工具

1. 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 本機登錄或 HKEY_CLASSES_ROOT 中的系統登錄中，註冊自訂工具 DLL。

    例如，以下是 managed MSDataSetGenerator 自訂工具的註冊資訊，隨附 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]：

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. 在所需的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hive 中建立登錄機碼 \\*guid* ，其中*guid*是特定語言的專案系統或服務所定義的 guid。 金鑰的名稱會成為自訂工具的程式設計名稱。 自訂工具鍵具有下列值：

   - (預設值)

        選擇項。 提供自訂工具的使用者易記描述。 這個參數是選擇性的，但建議使用。

   - CLSID

        必要項。 指定用來執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 之 COM 元件的類別庫識別碼。

   - GeneratesDesignTimeSource

        必要項。 指出是否將此自訂工具所產生之檔案的類型提供給視覺化設計工具。 此參數的值必須是（零）0，適用于視覺效果設計工具無法使用的類型，或（一）1適用于視覺化設計工具的類型。

   > [!NOTE]
   > 您必須針對想要使用自訂工具的每種語言，分別註冊自訂工具。

    例如，MSDataSetGenerator 會針對每個語言註冊一次：

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

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [實作單一檔案產生器](../../extensibility/internals/implementing-single-file-generators.md)
- [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [BuildManager 物件簡介](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
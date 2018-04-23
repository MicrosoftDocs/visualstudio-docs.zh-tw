---
title: Visual Studio 命令表 (。Vsct) 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3407c21f242cf45337ddad2ff19993d9e0130fbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio 命令表 (。Vsct) 檔案
命令資料表的組態檔是文字檔，描述一組之 VSPackage 所包含的命令。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令資料表 (VSCT) 編譯器會以 XML 為基礎的組態檔 （.vsct 檔案） 編譯成二進位的命令資料表輸出 (.cto) 檔案。 結果.cto 檔是與所建立所使用的命令資料表 (CTC) 編譯器來編譯.ctc 組態檔相同。 不過，XML.vsct 檔案有一些優點，例如 XML 編輯器和 XML IntelliSense。  
  
 若要深入了解的語法和語意.vsct 檔案，請參閱[設計 XML 命令資料表 (。Vsct) 檔案](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>本節內容  
 [設計 XML 命令表檔案 (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 描述如何設計.vsct 檔案。  
  
 [如何：建立 .Vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 比較方法來建立.vsct 檔。 描述以手動方式建立新的.vsct 檔的程序。  
  
## <a name="related-sections"></a>相關章節  
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)  
 提供有關每個區段的命令資料表 XML 組態檔的詳細資料。  
  
 [命令表格組態 (。Ctc) 檔案](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 顯示已被取代的.ctc 檔格式的概觀。  
  
 [VSPackage 如何新增使用者介面元素](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 描述命令資料表格式規格。  
  
 [VSPackage 中的資源](../../extensibility/internals/resources-in-vspackages.md)  
 描述如何使用 managed Vspackage 中的 managed 和 unmanaged 資源。  
  
 [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)  
 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。
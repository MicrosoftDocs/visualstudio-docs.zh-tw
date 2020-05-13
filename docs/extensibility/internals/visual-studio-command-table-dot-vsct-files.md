---
title: 視覺化工作室命令表 (.Vsct) 檔案 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704030"
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio 命令表檔案 (.Vsct)
指令表設定檔是描述 VSPackage 包含的命令集的文字檔。 命令[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]表 (VSCT) 編譯器將基於 XML 的設定檔 (.vsct 檔案) 編譯為二進位指令表輸出 (.cto) 檔。 產生的 .cto 檔案與使用指令表 (CTC) 編譯器編譯 .ctc 設定檔時創建的檔案相同。 但是,基於 XML 的 .vsct 檔具有一些優點,例如 XML 編輯器和 XML IntelliSense。

 要瞭解有關 .vsct 檔的語法和語義的更多內容,請參閱[設計 XML 命令表 (。Vsct) 檔案](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>本節內容
 [設計 XML 命令表檔案 (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 描述如何設計 .vsct 檔。

 [如何：建立 .Vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 比較建立 .vsct 檔案的方法。 描述手動創建新的 .vsct 文件的過程。

## <a name="related-sections"></a>相關章節
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)

 提供有關命令表 XML 配置檔的每個部分的詳細資訊。

 [指令表設定 (.Ctc) 檔案](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c)概述了已棄用的 .ctc 檔案格式。

 [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 描述命令表格式規範。

 [VSPackage 中的資源](../../extensibility/internals/resources-in-vspackages.md)

 介紹如何在託管 VS 包中使用託管和非託管資源。

 [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。

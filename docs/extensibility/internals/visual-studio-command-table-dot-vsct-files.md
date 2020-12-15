---
title: Visual Studio 命令表格 (。.Vsct) Files |Microsoft Docs
description: 瞭解命令表格設定檔，這是描述 VSPackage 所包含之命令集的文字檔。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 377bae52f506c1cb9ac0f6b2d4136faaab0b50ad
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488033"
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio 命令表檔案 (.Vsct)
命令表格設定檔是一個文字檔，描述 VSPackage 所包含的一組命令。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]命令表格 (.vsct) 編譯器會將 XML 架構設定檔 ( .vsct 檔案，) 到二進位命令表格輸出 (. cto) 檔中。 Cto 檔案與使用命令表格建立的檔案相同， (.CTC) 編譯器來編譯 .ctc 設定檔。 不過，以 XML 為基礎的 .vsct 檔案有一些優點，例如 XML 編輯器和 XML IntelliSense。

 若要深入瞭解 .vsct 檔案的語法和語義，請參閱[設計 XML 命令表格 (。.Vsct) ](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)檔案

## <a name="in-this-section"></a>本節內容
 [設計 XML 命令表檔案 (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 描述如何設計 .vsct 檔。

 [如何：建立 .Vsct 檔案](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 比較用來建立 .vsct 檔案的方法。 描述手動建立新 .vsct 檔案的程式。

## <a name="related-sections"></a>相關章節
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)

 提供命令表格 XML 設定檔的每個區段的詳細資料。

 [命令資料表設定 (。.Ctc) ](/previous-versions/bb165153(v=vs.100)) 檔案提供 .ctc 檔案格式的總覽。

 [VSPackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 描述命令表格格式規格。

 [VSPackage 中的資源](../../extensibility/internals/resources-in-vspackages.md)

 描述如何在 managed Vspackage 中使用受控和非受控資源。

 [命令、功能表及工具列](../../extensibility/internals/commands-menus-and-toolbars.md)

 說明如何建立包含功能表、工具列和命令下拉式方塊的 UI。
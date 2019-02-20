---
title: Help Content Manager 覆寫
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b881ee7a782d7c5f90a447c1719bb88afd1d332
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56314594"
---
# <a name="help-content-manager-overrides"></a>Help Content Manager 覆寫

您可以變更 Help Viewer 和 Visual Studio IDE 之說明相關功能的預設行為。 某些選項是透過建立 [.pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/) 檔案以設定各種登錄機碼值來指定。 其他選項則是在登錄中直接設定。

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>如何使用 .pkgdef 檔案控制 Help Viewer 行為

1. 建立 .pkgdef 檔案並以 `[$RootKey$\Help]` 作為第一行。

2. 分行加入下表中所述的任何或所有登錄機碼值，例如 `"UseOnlineHelp"=dword:00000001`。

3. 將檔案複製到 %ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<版本\>\Common7\IDE\CommonExtensions。

4. 在開發人員命令提示字元中執行 `devenv /updateconfiguration`。

### <a name="registry-key-values"></a>登錄機碼值

|登錄機碼值|類型|資料|描述|
|------------------|----|----|-----------|
|NewContentAndUpdateService|字串|\<服務端點的 HTTP URL\>|定義唯一的服務端點|
|UseOnlineHelp|dword|`0` 表示指定本機說明，`1` 表示指定線上說明|定義線上或離線說明預設值|
|OnlineBaseUrl|字串|\<服務端點的 HTTP URL\>|定義唯一的 F1 端點|
|OnlineHelpPreferenceDisabled|dword|`0` 表示啟用線上說明喜好設定選項，`1` 表示停用|停用線上說明喜好設定選項|
|DisableManageContent|dword|`0` 表示啟用 Help Viewer 中的 [管理內容] 索引標籤，`1` 表示停用|停用 [管理內容] 索引標籤|
|DisableFirstRunHelpSelection|dword|`0` 表示啟用第一次啟動 Visual Studio 時所設定的說明功能，`1` 表示停用|停用第一次啟動 Visual Studio 時所安裝的內容|

### <a name="example-pkgdef-file-contents"></a>.pkgdef 檔案內容範例

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>使用登錄編輯程式變更說明檢視器行為

您可以在登錄編輯程式中設定登錄機碼值，來控制下列兩種行為。

|工作|登錄機碼|值|資料|
|----------|-----|------|----|
|覆寫 BITS 工作優先權|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (在 64 位元電腦上)\Microsoft\Help\v2.3|BITSPriority|**前景**、**高**、**一般**或**低**|
|指向網路共用上的本機內容存放區|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>另請參閱

- [Help Viewer 系統管理員指南](../help-viewer/administrator-guide.md)
- [Help Content Manager 的命令列引數](../help-viewer/command-line-arguments.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
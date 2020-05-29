---
title: Visual Studio for Mac –整合式終端機
description: Visual Studio for Mac 提供整合式的開發環境，以在 macOS 上建置 .NET 應用程式，包括 ASP.NET Core 網站，和適用於 iOS、Android、Mac 和 Xamarin.Forms 的 Xamarin 專案。
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: d362938e8f0075591ea5d4ed8461d11395680b5c
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84185200"
---
# <a name="integrated-terminal"></a>整合式終端
在 Visual Studio for Mac 您可以開啟整合式終端機視窗，一開始是從解決方案的根目錄開始。 終端機會適用于不同類型的情況，也就是執行前端工作（例如： npm、ng 或 vue）、管理容器、執行 advanced git 命令、執行 Entity Framework 命令、查看 dotnet CLI 輸出、新增 NuGet 套件等等。 

若要開啟終端：
- 使用**Ctrl + '** 鍵盤快速鍵來顯示或隱藏終端機視窗。
- 使用 [ **View** \> **pad** ] \> **終端**機功能表。
- 使用 [搜尋] 列中的 [**終端**機] 命令。

![* 在啟動後立即 Visual Studio for Mac 整合式終端機。 *](media/integrated-terminal-intro.png)

根據預設，當終端機啟動時，它將會：
- 將工作目錄設定為目前解決方案的路徑。
- 載入預設的系統 shell。

## <a name="search"></a>搜尋
您可以使用 [**搜尋 > 尋找 ...** ] 功能表來搜尋終端機視窗的內容。

![* Visual Studio for Mac 整合式終端機中的搜尋體驗 *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>終端機鍵盤快速鍵
|命令|鍵盤快速鍵|
|-|-|
|顯示/隱藏終端機視窗|**Ctrl + '**|
|建立新的終端機實例|**Ctrl + '**|
|向上捲動頁面|**PageUp**|
|向下捲動頁面|**PageDown**|
|迴圈處理先前使用的命令|**↑**、 **↓**|
|增加字型大小|**則是⌘ +**|
|縮小字型大小|**則是⌘**|

## <a name="multiple-instances"></a>多個執行個體
終端機的多個實例隨時可能正在執行。 您可以使用**Ctrl + '** 鍵盤快速鍵來建立新的實例。 您可以按一下每個實例的索引標籤，或使用**Ctrl + tab**快捷方式來使用 [視窗選擇器] 對話方塊，以在實例之間切換。

![* Visual Studio for Mac 中的多個終端機實例 *](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>自訂終端機視窗
### <a name="configuring-the-terminal-font"></a>設定終端字型
您可以在 [> 環境 > 字型] 窗格的 [喜好設定] 中，變更用於終端機內容的字型和大小。 根據預設，字型會與輸出 Pad 內容相同，使用 Menlo 一般，大小11。 您可以將它設定為任何字型，而不受您的編輯器字型影響。

![* 自訂整合式終端機的字型設定 *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>重複使用系統終端機自訂
整合式終端機使用與 macOS 系統終端機相同的預設和設定。 這表示您的終端機自訂（zsh、zsh 等）也適用于整合式終端機。

---
title: Visual Studio for Mac-整合式終端機
description: Visual Studio for Mac 提供整合式的開發環境，以在 macOS 上建置 .NET 應用程式，包括 ASP.NET Core 網站，和適用於 iOS、Android、Mac 和 Xamarin.Forms 的 Xamarin 專案。
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: d362938e8f0075591ea5d4ed8461d11395680b5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "84185200"
---
# <a name="integrated-terminal"></a>整合式終端
在 Visual Studio for Mac 您可以開啟整合式終端機視窗，一開始先從解決方案的根目錄開始。 終端機適用于不同類型的情況-執行前端工作 (例如： npm、ng 或 vue) 、管理容器、執行 advanced git 命令、執行 Entity Framework 命令、觀看 dotnet CLI 輸出、新增 NuGet 套件等等。 

若要開啟終端：
- 使用 **Ctrl + '** 鍵盤快速鍵來顯示或隱藏終端機視窗。
- 使用 **View** \> **pad** \> **終端** 機功能表。
- 從搜尋列使用 **終端** 機命令。

![* 在啟動後立即 Visual Studio for Mac 整合式終端機。 *](media/integrated-terminal-intro.png)

依預設，當終端機啟動時，會：
- 將工作目錄設定為目前解決方案的路徑。
- 載入預設的系統 shell。

## <a name="search"></a>搜尋
您可以使用 [ **搜尋 > 尋找 ...** ] 功能表來搜尋終端機視窗的內容。

![* Visual Studio for Mac 整合式終端機中的搜尋體驗 *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>終端機鍵盤快速鍵
|命令|鍵盤快速鍵|
|-|-|
|顯示/隱藏終端機視窗|**Ctrl + '**|
|建立新的終端機實例|**Ctrl + '**|
|向上捲動頁面|**PageUp**|
|向下捲動頁面|**PageDown**|
|迴圈使用先前使用的命令|**↑**、 **↓**|
|增加字型大小|**⌘ +**|
|減少字型大小|**⌘**|

## <a name="multiple-instances"></a>多個執行個體
終端機的多個實例可能會在任何時間執行。 您可以使用 **Ctrl +** 鍵盤快速鍵來建立新的實例。 您可以按一下每個實例的索引標籤，或使用 **Ctrl + tab** 快速鍵來使用 [視窗選擇器] 對話方塊，以在實例之間切換。

![* Visual Studio for Mac 中的多個終端機實例 *](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>自訂終端機視窗
### <a name="configuring-the-terminal-font"></a>設定終端字型
您可以在 [喜好設定 > 環境] > 字型] 窗格中，變更用於終端機內容的字型和大小。 根據預設，字型將與輸出板內容相同，並使用 Menlo Regular，大小為11。 您可以將它設定為與編輯器字型無關的任何字型。

![* 自訂整合式終端機的字型設定 *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>重複使用系統終端機自訂
整合式終端機使用與 macOS 系統終端機相同的預設值和設定。 這表示您的終端機自訂 (zsh、喔-zsh 等 ) 也可在整合式終端機中運作。

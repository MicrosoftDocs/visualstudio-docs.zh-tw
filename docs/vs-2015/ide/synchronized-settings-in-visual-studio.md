---
title: 同步設定
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6459b6f65fd1e29fbadb01f6aa2fc51520b726b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646819"
---
# <a name="synchronized-settings-in-visual-studio"></a>Visual Studio 中的同步處理設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您使用相同的個人化帳戶在多部電腦上登入 Visual Studio 時，根據預設所有電腦皆會同步處理您的設定。

## <a name="synchronized-settings"></a>同步設定
 預設會同步處理下列設定。

- 開發設定 (您必須在第一次執行 Visual Studio 時選取一組設定，但是可以隨時變更選取範圍。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3))。

- [工具] &#124; [選項]  頁面中的下列選項：

  - [環境]  、[一般]  選項頁面上的 [主題]  和功能表列大小寫設定

  - [環境]  、[字型和色彩]  選項頁面上的所有設定

  - [環境]  、[鍵盤]  選項頁面上的所有鍵盤快速鍵

  - [環境]、[索引標籤和視窗]  選項頁面上的所有設定

  - [環境]  、[啟動]  選項頁面上的所有設定

  - [文字編輯器]  選項頁面上的所有設定

- [XAML 設計工具] 選項頁上的所有設定

- 使用者定義的命令別名。 如需如何定義命令別名的詳細資訊，請參閱 [Visual Studio 命令別名](../ide/reference/visual-studio-command-aliases.md)。

- [視窗] &#124; [管理視窗配置]  頁面中的使用者定義視窗配置

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>關閉特定電腦的同步設定
 Visual Studio 的同步設定預設為開啟。 您可以關閉電腦的同步設定，方法是移至 [工具] &#124; [選項] &#124; [環境] &#124; [同步設定]  頁面，並且取消核取核取方塊。  例如，如果您決定不要同步處理電腦 A 上 Visual Studio 的設定，則任何在電腦 A 上的設定變更都不會出現在電腦 B 或電腦 C 上。電腦 B 和 C 會繼續互相同步處理，但不會和電腦 A 同步。

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>同步處理 Visual Studio 系列產品和版本之間的設定
 可同步處理任何 Visual Studio 2015 版本之間的設定，包含 Express 與 Community 版本。 Visual Studio 系列產品中 (例如 Blend) 的設定也會同步處理。 不過，這些系列產品中的每一個都可能有它自己不會與 Visual Studio 共用的設定。 例如，電腦 A 的 Blend 專屬設定會和電腦 B 的 Blend 專屬設定共用，但不會和電腦 A 或 B 上的 Visual Studio 共用。

> [!WARNING]
> Visual Studio 2013 和 Visual Studio 2015 之間的設定不會同步處理。 第一次開啟 Visual Studio 2015 時，您 Visual Studio 2013 的設定會移轉過去，但之後將無法將其移轉回 Visual Studio 2013。

## <a name="see-also"></a>另請參閱
 [個人化 IDE](../ide/personalizing-the-visual-studio-ide.md)

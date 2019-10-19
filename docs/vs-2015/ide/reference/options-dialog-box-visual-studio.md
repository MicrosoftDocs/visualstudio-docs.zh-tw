---
title: 選項對話方塊 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ed637943d7a849357338593ffc684e4f45c09a30
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662438"
---
# <a name="options-dialog-box-visual-studio"></a>選項對話方塊 (Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[選項]  對話方塊可讓您依需求設定整合式的開發環境 (IDE)。 例如，您可以建立專案的預設儲存位置、改變視窗的預設外觀和行為，並建立常用命令的快速鍵。 也有開發語言與平台的專屬選項。 您可以從 [工具]  功能表存取 [選項]  。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊可用選項，以及功能表命令的名稱和位置，可能會與 [說明] 中描述的有所不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)

## <a name="layout-of-the-options-dialog-box"></a>[選項] 對話方塊的版面配置
 [選項]  對話方塊分為兩個部分︰左側的瀏覽窗格和右側的顯示區域。 瀏覽窗格中的樹狀控制項包含資料夾節點，例如 [環境]、[文字編輯器]、[專案和方案] 及 [原始檔控制]。 展開任何資料夾節點，列出其包含的選項頁。 當您選取特定頁面的節點時，其選項就會出現在顯示區域。

 在功能載入記憶體前，瀏覽窗格不會顯示 IDE 功能的選項。 因此，當您開始新的工作階段時，顯示的選項和您上個工作階段結束時所顯示的選項可能不一樣。 當您建立專案或執行使用特定應用程式的命令時，會在 [選項] 對話方塊中新增相關選項的節點。 只要 IDE 功能保留在記憶體中，就可以一直使用這些新增的選項。

> [!NOTE]
> 某些設定集合會設定 [選項] 對話方塊瀏覽窗格中顯示的頁數範圍。 您可以選取 [顯示所有設定]  選擇檢視所有可能的頁面。

## <a name="how-options-are-applied"></a>選項套用的方式
 按一下 [選項]  對話方塊的 [確定]，在所有頁面儲存所有設定。 按一下任何頁面的 [取消] 取消所有變更要求，包括任何只在其他 [選項]  頁面上進行的變更。 有些選項設定的變更，例如對[[字型和色彩]、[環境]、[選項]](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md) 等對話方塊進行的變更，只有在關閉並重新開啟 Visual Studio 之後才會生效。

### <a name="show-all-settings"></a>顯示所有設定
 選取或取消選取 [顯示所有設定]  適用於所有在 [選項]  對話方塊中進行的變更，即使您還沒按一下 [確定]  。

## <a name="see-also"></a>另請參閱
 [自訂編輯器](../../ide/customizing-the-editor.md)

---
title: 建立包含所有呼叫堆疊的小型傾印
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 8af2ef642a1c2422d470c716e14dca7d2e0168eb
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770846"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>建立包含所有呼叫堆疊的 Visual Studio 處理序小型傾印

在某些情況下，Microsoft 可能會要求執行中 Visual Studio 處理序的小型傾印，並附帶所有呼叫堆疊的資訊。 若要收集此資訊，請執行下列步驟：

## <a name="create-the-minidump-file"></a>建立小型傾印檔案

1. 啟動新的 Visual Studio 執行個體。
1. 從主功能表中，選擇 [ **Debug**] [  >  **附加至進程**]。
1. 勾選相關的 [受控]**** 和 [原生]**** 核取方塊，然後按 [附加]****。

   ![附加至處理序](../ide/media/attach-to-process.png)

1. 從正在執行的程序清單中，選取其他要附加的 Visual Studio 執行個體。
1. 從主功能表中 **，選擇 [**  >  **全部偵測中斷**]。
1. 從主功能表中，選擇 [ **Debug**  >  **Save Dump As**]。

## <a name="get-the-call-stacks-from-the-minidump"></a>從小型傾印中取得呼叫堆疊

1. 在 Visual Studio 開啟傾印檔案。
1. 移至 [**工具**  >  ] [**選項**]  >  [**調試**程式  >  **符號**]，並確定已核取 [符號檔 **（.pdb）位置**] 中的 [ **Microsoft 符號伺服器**]。
1. 開啟 [命令]**** 視窗 ([檢視]**** > [其他視窗]**** > [命令視窗]****)
1. 鍵入 ‘~*k’。 此視窗會顯示所有執行緒的呼叫堆疊。
1. 複製 [命令視窗] 中的所有文字，並儲存為文字檔案。
1. 將 txt 檔案附加至 Bug。

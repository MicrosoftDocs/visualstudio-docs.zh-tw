---
title: 限制檢測特定 DLL | Microsoft Docs
description: 瞭解如何使用檢測程式碼剖析方法，將程式碼剖析資料的收集限制為應用程式中的一或多個 Dll。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 170a701e4eb8d42a15a475b1336a0ba33c20b01a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860772"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>如何：限制檢測特定 DLL

您可以藉由使用檢測程式碼剖析方法，將程式碼剖析資料的收集限制在應用程式中的一或多個 DLL。 若要分析應用程式中的一個或多個 Dll，您可以建立包含的效能會話。做為目標的 *dll* 檔案。 您可以將要進行分析的 DLL 指定成 Visual Studio 方案中的專案，或是指定成獨立的二進位檔案。

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>限制檢測 Visual Studio 方案中的特定 DLL

1. 在 Visual Studio 中開啟包含該 DLL 的方案。

2. 選取 [分析] 功能表上的 [啟動效能精靈]。

3. 選擇 [檢測] 做為程式碼剖析方法，然後按 [下一步]。

4. 從 **下列哪些可用的目標中，您想要進行分析？**，選取的名稱。*dll* 專案，然後按 **[下一步]**。

5. 按一下 [完成] 結束精靈，並將新的效能工作階段顯示在 [效能總管] 視窗中。

6. 以滑鼠右鍵按一下 [目標]，然後選取 [加入目標專案]。

7. 從 [加入目標專案] 清單中，選取您要用來執行 DLL 的可執行專案。

     選擇性。 您可以加入要進行程式碼剖析的其他任何 DLL 專案。

8. 如果不要對某個已加入的專案收集資料，請以滑鼠右鍵按一下該專案的名稱，然後再清除 [檢測] 核取方塊。

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>將要進行程式碼剖析的特定 DLL 指定成獨立的二進位檔

1. 開啟 Visual Studio。

2. 選取 [分析] 功能表上的 [啟動效能精靈]。

3. 從 [您要對下列哪一項可用目標進行程式碼剖析]，選取 [為動態連結程式庫 (.DLL) 進行程式碼剖析]，然後按 [下一步]。

4. 在精靈的第二頁執行下列步驟：

    - 輸入的路徑和檔案名。您要在 **dll 路徑** 中進行程式碼剖析的 *dll* 檔案。 您也可以按一下省略符號按鈕 (...)，在 [要進行程式碼剖析的動態連結程式庫] 對話方塊中尋找檔案。 請注意，您必須指定的複本。可執行檔 ( 將啟動的 *dll* 檔案。您接下來選取的 *exe*) 檔案。

    - 輸入可執行檔 ( 的路徑和檔案名。將在其中執行的 *exe*) 檔案。**可執行檔路徑** 中的 *dll* 。 您也可以按一下省略符號按鈕 (...)，在 [要啟動的可執行檔] 對話方塊中尋找檔案。

    - 選擇性。 在 [命令列的引數] 中，輸入要傳給可執行檔的任何命令列引數。 如有必要，請在 [工作目錄] 中指定應用程式的工作目錄。

    - 按一下 [下一步] 。

5. 選擇 [檢測] 做為程式碼剖析方法，然後按 [下一步]。

6. 按一下 [完成] 結束精靈，並將新的效能工作階段顯示在 [效能總管] 視窗中。

7. 選擇性。 以加入更多。*dll* 檔案，以滑鼠右鍵按一下 [ **目標** ]，然後選取 [ **加入目標二進位** 檔]。 接著再從 [加入目標二進位檔] 對話方塊選取檔案。

    > [!NOTE]
    > 請勿指定可執行檔 (。執行 Dll 的 *exe*) 檔。

## <a name="see-also"></a>另請參閱

[控制資料收集](../profiling/controlling-data-collection.md) 
[如何：限制檢測特定](../profiling/how-to-limit-instrumentation-to-specific-functions.md)函式

---
title: "如何：限制檢測特定 DLL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3ad8aaf7dbf9960a3281add90da685c2942bd179
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>如何：限制檢測特定 DLL
您可以藉由使用檢測程式碼剖析方法，將程式碼剖析資料的收集限制在應用程式中的一或多個 DLL。 若要對應用程式中的一或多個 DLL 進行程式碼剖析，請建立包含 .dll 檔案做為目標的效能工作階段。 您可以將要進行程式碼剖析的 DLL，指定成 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案中的專案，或是指定成獨立的二進位檔案。  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>限制檢測 Visual Studio 方案中的特定 DLL  
  
1.  在 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] 中開啟包含 DLL 的方案。  
  
2.  選取 [分析] 功能表上的 [啟動效能精靈]。  
  
3.  選擇 [檢測] 做為程式碼剖析方法，然後按 [下一步]。  
  
4.  從 [您要對下列哪一項可用目標進行程式碼剖析?]，選取 .dll 專案的名稱，然後按 [下一步]。  
  
5.  按一下 [完成] 結束精靈，並將新的效能工作階段顯示在 [效能總管] 視窗中。  
  
6.  以滑鼠右鍵按一下 [目標]，然後選取 [加入目標專案]。  
  
7.  從 [加入目標專案] 清單中，選取您要用來執行 DLL 的可執行專案。  
  
     選擇性。 您可以加入要進行程式碼剖析的其他任何 DLL 專案。  
  
8.  如果不要對某個已加入的專案收集資料，請以滑鼠右鍵按一下該專案的名稱，然後再清除 [檢測] 核取方塊。  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>將要進行程式碼剖析的特定 DLL 指定成獨立的二進位檔  
  
1.  開啟 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]。  
  
2.  選取 [分析] 功能表上的 [啟動效能精靈]。  
  
3.  從 [您要對下列哪一項可用目標進行程式碼剖析]，選取 [為動態連結程式庫 (.DLL) 進行程式碼剖析]，然後按 [下一步]。  
  
4.  在精靈的第二頁執行下列步驟：  
  
    -   在 [DLL 路徑] 中，輸入要進行程式碼剖析之 .dll 檔案的路徑和檔名。 您也可以按一下省略符號按鈕 (...)，在 [要進行程式碼剖析的動態連結程式庫] 對話方塊中尋找檔案。 請注意，您必須指定接下來選取之可執行檔 (.exe) 所啟動的那份 .dll 檔案。  
  
    -   在 [可執行檔路徑] 中，輸入要執行 .dll 之可執行檔 (.exe) 的路徑和檔名。 您也可以按一下省略符號按鈕 (...)，在 [要啟動的可執行檔] 對話方塊中尋找檔案。  
  
    -   選擇性。 在 [命令列的引數] 中，輸入要傳給可執行檔的任何命令列引數。 如有必要，請在 [工作目錄] 中指定應用程式的工作目錄。  
  
    -   按 [ **下一步**]。  
  
5.  選擇 [檢測] 做為程式碼剖析方法，然後按 [下一步]。  
  
6.  按一下 [完成] 結束精靈，並將新的效能工作階段顯示在 [效能總管] 視窗中。  
  
7.  選擇性。 若要加入其他 .dll 檔案，請以滑鼠右鍵按一下 [目標]，然後選取 [加入目標二進位檔]。 接著再從 [加入目標二進位檔] 對話方塊選取檔案。  
  
    > [!NOTE]
    >  請勿指定執行 DLL 的可執行檔 (.exe)。  
  
## <a name="see-also"></a>請參閱  
 [控制資料收集](../profiling/controlling-data-collection.md)   
 [如何：限制檢測特定函式](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
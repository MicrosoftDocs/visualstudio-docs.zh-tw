---
title: "建立單元測試專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: "8"
ms.author: douge
manager: douge
ms.openlocfilehash: a064d56a0be2acf6000a9e7da770cb9b25d3b65f
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="create-a-unit-test-project"></a>建立單元測試專案
單元測試通常會反映測試之程式碼的結構。 例如，單元測試專案會針對產品中的每個程式碼專案建立。 測試專案可位於與實際程式碼相同的方案中，或位於其他方案中。 您在方案中可以有多個單元測試專案。  
  
> [!NOTE]
>  機器碼的單元測試位置和測試專案結構可能會與本主題中所描述的結構不同。 如需詳細資訊，請參閱[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)。  
  
## <a name="to-create-a-unit-test-project"></a>建立單元測試專案：  
  
1.  在 [檔案]  功能表上，選擇 [新增]  ，然後選擇 [專案] \(鍵盤 Ctrl + Shift + N)。  
  
2.  在 [新增專案] 對話方塊中，展開 [已安裝] 節點，選擇您想要用於測試專案的語言，然後選擇 [測試]。  
  
3.  若要使用其中一個 Microsoft 單元測試架構，請從專案範本清單中選擇 [單元測試專案]  。 否則，請選擇您所要使用單元測試架構的專案範本。 若要測試本範例的 Accounts 專案，您要將專案命名為 AccountsTests。  
  
4.  在單元測試專案中，加入受測程式碼的參考。  以下是在相同方案中建立程式碼專案參考的方式：  
  
    1.  在 [方案總管] 中選取專案。  
  
    2.  在 [專案] 功能表上，選擇 [加入參考]。  
  
    3.  在 [參考管理員] 對話方塊上，開啟 [方案] 節點，然後選擇 [專案]。 檢查程式碼專案名稱，然後關閉對話方塊。  
  
5.  如果您要測試的程式碼在另一個位置，請參閱[管理專案中的參考](../ide/managing-references-in-a-project.md)了解加入參考的相關資訊。  
  
## <a name="next-steps"></a>後續步驟  
 **撰寫單元測試**  
  
 查看下列其中一個小節：  
  
-   [使用適用於 Managed 程式碼的 Microsoft 單元測試架構撰寫適用於 .NET Framework 的單元測試](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
-   [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)  
  
 **執行單元測試**  
  
 [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)

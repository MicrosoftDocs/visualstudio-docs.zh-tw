---
title: "以 64 位元處理序的形式執行單元測試 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: "25"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 39addca0d673ae5a9423d4195ffc2bfe3358de4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>以 64 位元處理序的形式執行單元測試
如果您有 64 位元的電腦，即可透過 64 位元處理序的形式執行單元測試並擷取程式碼涵蓋範圍資訊。  
  
## <a name="running-a-unit-test-as-a-64-bit-process"></a>以 64 位元處理序的形式執行單元測試  
  
#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>若要以 64 位元處理序的形式執行單元測試  
  
1.  如果您的程式碼或測試已編譯為 32 位元/x86，但現在想以 64 位元處理序的形式來執行，請將它們重新編譯為 [任何 CPU]，或選擇重新編譯為 [64 位元]。  
  
    > [!TIP]
    >  為了達到最大彈性，您應該使用 [任何 CPU] 組態來編譯測試專案。 然後，您就可以在 32 和 64 位元代理程式上執行。 使用 [64 位元] 組態來編譯測試專案並沒有任何優點。  
  
2.  從 Visual Studio 功能表中，選擇 [測試]，然後依序選擇 [設定] 和 [處理器架構]。 選擇 [x64]，以 64 位元處理序的形式來執行測試。  
  
     \-或-  
  
     在 .runsettings 檔案中指定 `<TargetPlatform>x64</TargetPlatform>`。 這個方法的優點是，您可以指定不同檔案中的設定群組，並且在不同設定之間快速切換。 您也可以在方案之間複製設定。 如需詳細資訊，請參閱[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)   
 [對程式碼進行單元測試](../test/unit-test-your-code.md)   
 [指定 Visual Studio 測試的測試設定](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)

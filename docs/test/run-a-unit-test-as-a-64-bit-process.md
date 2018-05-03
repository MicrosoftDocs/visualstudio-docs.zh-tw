---
title: 在 Visual Studio 中以 64 位元處理序的形式執行單元測試
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2b6e44ae9b0587a044cb1a8a0d62db068dfc76d6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>以 64 位元處理序的形式執行單元測試

如果您有 64 位元的電腦，即可透過 64 位元處理序的形式執行單元測試並擷取程式碼涵蓋範圍資訊。

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>若要以 64 位元處理序的形式執行單元測試

1. 如果您的程式碼或測試已編譯為 32 位元/x86，但現在想以 64 位元處理序的形式來執行，請將它們重新編譯為 [任何 CPU]，或選擇重新編譯為 [64 位元]。

    > [!TIP]
    > 為了達到最大彈性，請使用 [任何 CPU] 組態來編譯測試專案。 然後，您就可以在 32 位元和 64 位元代理程式上執行。 使用 [64 位元] 組態來編譯測試專案並沒有任何優點。

2. 從 Visual Studio 功能表中，選擇 [測試]，然後依序選擇 [設定] 和 [處理器架構]。 選擇 [x64]，以 64 位元處理序的形式來執行測試。

   - 或 -

   在 *.runsettings* 檔案中指定 `<TargetPlatform>x64</TargetPlatform>`。 這個方法的優點是，您可以指定不同檔案中的設定群組，並且在不同設定之間快速切換。 您也可以在方案之間複製設定。 如需詳細資訊，請參閱[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。

## <a name="see-also"></a>另請參閱

- [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)
- [對程式碼進行單元測試](../test/unit-test-your-code.md)

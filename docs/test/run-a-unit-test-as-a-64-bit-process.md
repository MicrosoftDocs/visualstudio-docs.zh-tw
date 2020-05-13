---
title: 以 64 位元處理序的形式執行單元測試
ms.date: 03/10/2020
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d6c6839f8c4702d88d1022116231c6f22b5dbf21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093909"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>以 64 位元處理序的形式執行單元測試

如果您有 64 位元的電腦，即可透過 64 位元處理序的形式執行單元測試並擷取程式碼涵蓋範圍資訊。

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>若要以 64 位元處理序的形式執行單元測試

1. 如果代碼或測試編譯為 32 位/x86，但現在要將它們作為 64 位進程運行，請將其重新編譯為**任何 CPU**。

   ::: moniker range="vs-2017"
   或者，在 Visual Studio 2017 中，您還可以將專案編譯為**64 位**。
   ::: moniker-end

    > [!TIP]
    > 為了達到最大彈性，請使用 [任何 CPU]**** 組態來編譯測試專案。 然後，您就可以在 32 位元和 64 位元代理程式上執行。 使用 [64 位元]**** 組態來編譯測試專案並沒有任何優點。

2. 將單元測試設置為 64 位進程運行。

   ::: moniker range=">=vs-2019"
   從 Visual Studio 功能表中，選擇 **"測試**"，然後為**AnyCPU 專案選擇處理器體系結構**。 選擇 [x64]****，以 64 位元處理序的形式來執行測試。
   ::: moniker-end
   ::: moniker range="vs-2017"
   從視覺化工作室功能表中，選擇 **"測試**"，然後選擇 **"測試設定**"，然後選擇 **"處理器架構**"。 選擇 [x64]****，以 64 位元處理序的形式來執行測試。
   ::: moniker-end

   \- 或 -

   在 *.runsettings* 檔案中指定 `<TargetPlatform>x64</TargetPlatform>`。 這個方法的優點是，您可以指定不同檔案中的設定群組，並且在不同設定之間快速切換。 您也可以在方案之間複製設定。 如需詳細資訊，請參閱[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。

## <a name="see-also"></a>另請參閱

- [使用測試資源管理器運行單元測試](../test/run-unit-tests-with-test-explorer.md)
- [單元測試代碼](../test/unit-test-your-code.md)

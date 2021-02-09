---
title: 以 64 位元處理序的形式執行單元測試
description: 瞭解如何執行單元測試，並以64位進程的形式來捕捉程式碼涵蓋範圍資訊。 您必須有64位的電腦。
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 184ea2250732bfa37f1740fadfa85616d83a88cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917551"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>以 64 位元處理序的形式執行單元測試

如果您有 64 位元的電腦，即可透過 64 位元處理序的形式執行單元測試並擷取程式碼涵蓋範圍資訊。

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>若要以 64 位元處理序的形式執行單元測試

1. 如果您的程式碼或測試編譯為32位/x86，但您現在想要以64位進程的形式執行，請將它們重新編譯為 **任何 CPU**。

   ::: moniker range="vs-2017"
   或者，在 Visual Studio 2017 中，您也可以將專案編譯為 **64** 位。
   ::: moniker-end

    > [!TIP]
    > 為了達到最大彈性，請使用 [任何 CPU] 組態來編譯測試專案。 然後，您就可以在 32 位元和 64 位元代理程式上執行。 使用 **64** 位設定來編譯測試專案並沒有任何好處，除非您呼叫的程式碼只在64位上受到支援。

2. 將單元測試設定為以64位進程的形式執行。

   ::: moniker range=">=vs-2019"
   在 [Visual Studio] 功能表中，選擇 [ **測試**]，然後選擇 [ **AnyCPU 專案的處理器架構**]。 選擇 [x64]，以 64 位元處理序的形式來執行測試。
   ::: moniker-end
   ::: moniker range="vs-2017"
   在 [Visual Studio] 功能表中，選擇 [ **測試**]，然後選擇 [ **測試設定**]，再選擇 [ **處理器架構**]。 選擇 [x64]，以 64 位元處理序的形式來執行測試。
   ::: moniker-end

   \- 或 -

   在 *.runsettings* 檔案中指定 `<TargetPlatform>x64</TargetPlatform>`。 這個方法的優點是，您可以指定不同檔案中的設定群組，並且在不同設定之間快速切換。 您也可以在方案之間複製設定。 如需詳細資訊，請參閱[使用 .runsettings 檔案設定單元測試](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)。

## <a name="see-also"></a>另請參閱

- [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)
- [對程式碼進行單元測試](../test/unit-test-your-code.md)

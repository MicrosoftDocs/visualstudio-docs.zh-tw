---
title: 逐步解說：使用分析工具 API | Microsoft Docs
description: 瞭解如何使用 profiler Api 來限制檢測分析期間所收集的資料量。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e1405169ae7f4734463428405cf90cce631fba3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915944"
---
# <a name="walkthrough-using-profiler-apis"></a>逐步解說：使用分析工具 API

本逐步解說會使用 C# 應用程式示範如何使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具 API。 您將使用分析工具 API 來限制檢測分析期間所收集的資料量。

 本逐步解說中的步驟一般適用於 C/C++ 應用程式。 針對每一種語言，您必須適當地設定建置環境。

 一般而言，您會使用樣本分析開始分析應用程式效能。 如果範例分析未提供可指出瓶頸的資訊，檢測分析可以提供更高的詳細程度。 檢測分析十分適用於調查執行緒互動。

 不過，更詳細的層級表示會收集更多資料。 您可能會發現檢測分析會建立大型資料檔案。 此外，檢測更可能會影響應用程式的效能。 如需詳細資訊，請參閱[認識檢測資料值](../profiling/understanding-instrumentation-data-values.md)和[認識取樣資料值](../profiling/understanding-sampling-data-values.md)

 Visual Studio 分析工具可讓您限制資料收集。 本逐步解說所提供的範例說明如何使用分析工具 API 來限制資料收集。 Visual Studio 分析工具提供用於控制應用程式內資料收集的 API。

 ::: moniker range="vs-2017"
 針對機器碼，Visual Studio 分析工具 API 位在 *VSPerf.dll* 中。 標頭檔 (*VSPerf.h*) 和匯入程式庫 (*VSPerf.lib*) 位在 *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* 目錄中。  針對 64 位元應用程式，資料夾為 *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK*
 ::: moniker-end

 針對 managed 程式碼，profiler Api 位於 *Microsoft.VisualStudio.Profiler.dll* 中。 這個 DLL 位於 *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* 目錄。 針對 64 位元應用程式，資料夾為 *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*。 如需詳細資訊，請參閱[分析工具](/previous-versions/ms242704(v=vs.140))。

## <a name="prerequisites"></a>必要條件
 本逐步解說假設您所選擇的開發環境設定成支援偵錯和取樣。 下列主題概述這些必要條件：

- [如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)

- [如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)

 根據預設，啟動分析工具時，分析工具會收集全域層級的資料。 程式開頭的下列程式碼會關閉全域分析。

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 您可以在命令列關閉資料收集，而不使用 API 呼叫。 下列步驟假設您的命令列建置環境設定成執行分析工具和您的開發工具。 這包含 VSInstr 和 VSPerfCmd 所需的設定。 請參閱 [命令列程式碼剖析工具](../profiling/using-the-profiling-tools-from-the-command-line.md)。

## <a name="limit-data-collection-using-profiler-apis"></a>使用分析工具 API 限制資料收集

#### <a name="to-create-the-code-to-profile"></a>建立要分析的程式碼

1. 根據您的喜好設定，在 Visual Studio 中建立新的 C# 專案，或使用命令列組建。

    > [!NOTE]
    > 您的組建必須參考 *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* 目錄中的 *Microsoft.VisualStudio.Profiler.dll* 程式庫。

2. 複製下列程式碼，並將其貼入專案中：

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using Microsoft.VisualStudio.Profiler;

    namespace ConsoleApplication1
    {
        class Program
        {
            public class A
            {
                private int _x;

                public A(int x)
                {
                    _x = x;
                }

                public int DoNotProfileThis()
                {
                    return _x * _x;
                }

                public int OnlyProfileThis()
                {
                    return _x + _x;
                }

                public static void Main()
                {
                    DataCollection.StopProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    A a = new A(2);
                    Console.WriteLine("2 square is {0}", a.DoNotProfileThis());

                    DataCollection.StartProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    int x;
                    x = a.OnlyProfileThis();

                    DataCollection.StopProfile(
                    ProfileLevel.Global,
                    DataCollection.CurrentId);

                    Console.WriteLine("2 doubled is {0}", x);
                }
            }

        }
    }
    ```

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中收集和檢視資料

1. 開啟 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE。 在 [ **分析** ] 功能表上，指向 [ **Profiler**]，然後選取 [ **新增效能會話**]。

2. 在 [效能總管] 視窗中，將已編譯的二進位檔新增至 [目標] 清單。 以滑鼠右鍵按一下 [目標]，然後選取 [新增目標二進位檔]。 在 [新增目標二進位檔] 對話方塊中，找到二進位檔，然後按一下 [開啟]。

3. 在 [效能總管] 工具列的 [方法] 清單中，選取 [檢測]。

4. 按一下 [啟動並啟用分析]。

    分析工具會檢測和執行二進位檔，並建立效能報表檔案。 效能報表檔案會出現在 [效能總管] 的 [報表] 節點中。

5. 開啟產生的效能報表檔案。

   根據預設，啟動分析工具時，分析工具將會收集全域層級的資料。 程式開頭的下列程式碼會關閉全域分析。

```csharp
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>在命令列收集和檢視資料

1. 編譯您在本逐步解說前面的「建立要分析的程式碼」程序中所建立範例程式碼的偵錯版本。

2. 若要分析 Managed 應用程式，請鍵入下列命令，以設定適當的環境變數：

     **VsPerfCLREnv/traceon**

3. 輸入下列命令： **VSInstr \<filename> .exe**

4. 輸入下列命令： **>vsperfcmd/start： trace/output： \<filename> .vsp**

5. 輸入下列命令： **VSPerfCmd /globaloff**

6. 執行程式。

7. 輸入下列命令：**VSPerfCmd /shutdown**

8. 輸入下列命令： **VSPerfReport/calltrace： \<filename> .vsp**

     的.使用產生的效能資料，在目前的目錄中建立 *csv* 檔案。

## <a name="see-also"></a>另請參閱

- [程式碼剖析工具](/previous-versions/ms242704(v=vs.140))
- [Visual Studio profiler API 參考 (原生) ](../profiling/visual-studio-profiler-api-reference-native.md)
- [開始使用](../profiling/getting-started-with-performance-tools.md)
- [從命令列進行分析](../profiling/using-the-profiling-tools-from-the-command-line.md)

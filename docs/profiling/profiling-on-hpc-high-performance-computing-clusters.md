---
title: 在 HPC (高效能運算) 叢集上進行程式碼剖析 | Microsoft Docs
description: 瞭解如何使用 Visual Studio 分析工具的取樣方法，在 Microsoft Windows HPC 叢集的計算節點上進行分析。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06a160adda25debe21d8262d9064c23849011dc9
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720523"
---
# <a name="profile-on-hpc-high-performance-computing-clusters"></a>在 HPC (高效能運算) 叢集上進行分析

您可以使用 Visual Studio 分析工具的取樣方法，在 Microsoft Windows HPC 叢集的計算節點上進行分析。 如需有關 HPC 的詳細資訊，請參閱 Microsoft 網站上的 [Windows HPC](https://azure.microsoft.com/solutions/big-compute/)。

## <a name="prerequisites"></a>Prerequisites

若要在 HPC 計算節點上進行程式碼剖析，您必須執行下列動作︰

- 在 Visual Studio 所在的同一部電腦上安裝 Microsoft HPC Pack 2008。 電腦不一定要是 HPC 叢集的一部分。 您可以在 [Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=4812)安裝 HPC Pack。

- 在 HPC 計算節點上安裝 .NET Framework 4 和獨立版本的分析工具。 適用於 .NET Framework 和獨立分析工具的安裝程式均於 Visual Studio 安裝媒體上提供。 **注意**：您必須在安裝 .NET Framework 之後，以及在安裝分析工具之前重新啟動電腦。

  若要在作用中的 HPC 計算節點上安裝 .NET Framework 4 和獨立分析工具，並在叢集電腦上啟用分析功能，請依照下列步驟執行：

1. 開啟隨 HPC Pack 安裝的命令提示字元視窗。

2. 在個別的命令提示中輸入下列命令：

    1. `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`

    2. `clusrun /all /scheduler:`*% 前端節點%*`shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`

| | |
|------------------| - |
| *頭* | 叢集前端節點的名稱。 |
| *%FxPath%* | .NET Framework 4 安裝程式的路徑。 在 Visual Studio 安裝媒體的路徑是︰WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe |
| *%ProfilerPath%* | 獨立版本的程式碼剖析工具安裝程式路徑。 在 Visual Studio 安裝媒體的路徑是︰Standalone Profiler\x64\vs_profiler.exe |

## <a name="profile-on-an-hpc-compute-node"></a>在 HPC 計算節點上進行分析

您可以使用 HPC 效能精靈來指定 HPC 叢集和目標資訊，以設定程式碼剖析工作階段。 您可以在效能工作階段屬性頁中指定其他選項。 程式碼剖析工具會自動部署必要的目標二進位檔，並啟動分析工具和 HPC 應用程式。

1. 按一下 [分析] 功能表上的 [啟動 HPC 效能精靈]。 如果命令無法使用，請確定您擁有上面所列的必要條件。

2. 在精靈的第一個頁面上，按 [下一步] 。

3. 在精靈的第二個頁面上，選取您要進行程式碼剖析的應用程式。

   - 若要對目前在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 中開啟的專案進行程式碼剖析，請選取 [一個或多個可用的專案] 選項，然後從清單中選取專案名稱。

   - 若要進行程式碼剖析的二進位檔不在開啟專案中，請選取 [可執行檔 (.EXE 檔)] 選項。

4. 按一下 [下一步] 。

5. 在精靈的第三個頁面上：

    - 如果您正在進行程式碼剖析的可執行檔不是在開啟專案中，請在 [可執行檔的完整路徑為何] 中指定二進位檔的路徑。

    - 如果您正在進行程式碼剖析的可執行檔不是在開啟專案中，您可以在 [命令列引數] 中指定任何命令列引數，以傳遞至處理序。

    - 在 [遠端工作目錄] 中，指定由個別計算節點上處理序執行個體使用的資料夾路徑。

    - 在 [部署位置] 中，指定 HPC 伺服器用以佈置部署映像的目錄路徑。

6. 按一下 [下一步] 。

7. 在精靈的第四個頁面上：

    - 在 [前端節點] 清單中，按一下可在執行程式碼剖析時做為 HPC 前端節點的電腦。 前端節點可以是 "localhost"，這可讓您在本機電腦上進行程式碼剖析，而不需要叢集。

    - 在 [處理序數目] 清單中，按一下要執行的應用程式執行個體數目。

    - 從 [程式碼剖析選項] 清單中，選取程式碼剖析目標。

         若要對叢集中的特定處理序進行程式碼剖析，請選取 [依順序排列的設定檔] 選項，然後從下拉式清單中選取處理序的順位。

         若要進行程式碼剖析的處理序在 HPC 叢集中特定節點上執行，請選取 [依節點排列的設定檔] 選項，然後從下拉式清單中選取該節點。

8. 按一下 [下一步] 。

9. 在精靈的第五個頁面上，您可以選擇立即啟動分析工具和程式碼剖析處理序，或稍後使用 [效能總管] 來啟動程式碼剖析。

    - 選取 [在精靈完成後啟動分析] 以立即啟動程式碼剖析，或清除該核取方塊以手動方式啟動程式碼剖析。

10. 按一下 [完成] 。

## <a name="set-hpc-profiling-properties-by-using-performance-session-property-pages"></a>使用效能工作階段屬性頁來設定 HPC 程式碼剖析屬性

您可以在效能工作階段屬性頁的 [HPC 啟動屬性] 頁面上，變更在 HPC 程式碼剖析精靈上設定的效能工作階段屬性。 您可以在 [HPC 進階屬性] 頁面上設定其他選項。

### <a name="to-open-the-performance-session-property-pages"></a>開啟效能工作階段屬性頁

1. 如有必要，請在 [效能總管] 中開啟效能工作階段 (.psess) 檔案。 在 [檔案] 功能表上，按一下 [開啟]，然後選擇檔案。

2. 在效能總管中，以滑鼠右鍵按一下效能會話名稱，然後按一下 [ **屬性**]。

3. 在 [屬性頁] 對話方塊中，請使用下列其中一種方法：

    - 按一下 [一般]，然後選取 [在 HPC 叢集上收集]，以開啟 HPC 程式碼剖析，或清除該核取方塊以停用 HPC 程式碼剖析。

    - 按一下 [HPC 啟動屬性] 以變更啟動 HPC 應用程式的屬性。

    - 按一下 [HPC 進階屬性] 以設定其他選項

### <a name="hpc-launch-properties"></a>HPC 啟動屬性

|屬性|描述|
|--------------|-----------------|
|**前端節點**|指定可在執行程式碼剖析時做為 HPC 前端節點的電腦。|
|**處理序數目**|指定要在已進行程式碼剖析的應用程式中執行的應用程式執行個體數目。|
|**依順序排列的設定檔**|若要對叢集中的特定處理序進行程式碼剖析，請選取 [依順序排列的設定檔] 選項，然後從下拉式清單中選取處理序的順位。|
|**依節點排列的設定檔**|若要進行程式碼剖析的處理序在 HPC 叢集中特定節點上執行，請選取 [依節點排列的設定檔] 選項，然後從下拉式清單中選取該節點。|
|**遠端工作目錄**|指定由個別計算節點上處理序執行個體使用的資料夾路徑。|
|**部署位置**|指定 HPC 伺服器用以佈置部署映像的目錄路徑。|

### <a name="advanced-properties"></a>進階屬性

| 屬性 | 描述 |
|---------------------------------------| - |
| **專案名稱** | 目前 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 專案或解決方案的名稱。 |
| **於分析工具停止時清除** | 為 true 時，會將已部署至執行目錄的二進位檔移除。 此步驟不會移除由使用者程式建立的檔案和目錄。 如果是由 IDE 建立執行目錄和部署目錄，IDE 會嘗試加以移除，但不是由 IDE 所部署的檔案，則不會嘗試移除。 |
| **其他要部署的檔案** | 以分號分隔清單指定任何其他檔案，以部署在計算節點上。 您可以按一下省略符號按鈕 (**...**)，使用對話方塊來選取多個檔案。 |
| **MPIExec 命令** | 指定會啟動 MPI 應用程式的應用程式。 預設值為 **mpiexec.exe** |
| **MPIExec 引數** | 指定要傳遞至 mpiexec.exe 命令的引數。 |
| **叢集上的要求節點** | 在執行應用程式的叢集上，指定節點數目。 |
| **部署 CRT 檔案** | 為 true 時，在叢集上部署 C/C++ 執行階段。 |
| **剖析前指令碼** | 在程式碼剖析工作階段開始之前，指定要在本機開發電腦上執行指令碼的路徑和檔案名稱。 |
| **剖析前指令碼引數** | 指定要傳遞至剖析前指令碼的引數。 |
| **剖析後指令碼** | 在程式碼剖析工作階段結束之後，指定要在本機開發電腦上執行指令碼的路徑和檔案名稱。 |
| **剖析後指令碼引數** | 指定要傳遞至剖析後指令碼的引數。 |

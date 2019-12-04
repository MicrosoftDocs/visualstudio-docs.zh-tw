---
title: 如何：從命令列指定符號檔位置 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b4c4230ca2539b55f57990b90ae33d1f53726dc
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778722"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>如何：從命令列指定符號檔位置
若要顯示符號資訊 (例如函式名稱和行號)，VSPerfReport 命令列工具需要存取已進行程式碼剖析之元件的符號 (.*pdb*) 檔案和 Windows 系統檔。 符號檔是在元件編譯時建立。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。 VSPerfReport 會自動搜尋下列位置中是否有符號檔：

- **/SymbolPath** 選項或 **_NT_SYMBOL_PATH** 環境變數中指定的路徑。

- 編譯元件所在的確切本機路徑。

- 包含程式碼剖析資料 (.*vsp* 或 .*vsps*) 檔案的目錄。

  Microsoft 在符號伺服器中為許多產品線提供 .*pdb* 檔。 如果您用於回報的電腦已連接網際網路，VSPerfReport 會連接到線上符號伺服器以自動查閱符號資訊，並且將檔案儲存至本機存放區。

  您可以透過下列方式指定符號檔的位置以及 Microsoft 符號伺服器存放區：

- 設定 **_NT_SYMBOL_PATH** 環境變數。

- 將 **/SymbolPath** 選項加入至 VSPerfReport 命令列。

  您也可以同時使用這兩種方法。

> [!NOTE]
> 如果 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安裝在本機電腦上，則可能已指定 Windows 符號檔的位置。 如需詳細資訊，請參閱[如何：參考 Windows 符號資訊](../profiling/how-to-reference-windows-symbol-information.md)。 您仍然必須遵循本主題稍後所述的方式來設定 VSPerfReport 使用位置和伺服器。

## <a name="specify-windows-symbol-files"></a>指定 Windows 符號檔案

#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>設定使用 Windows 符號伺服器

1. 如有需要，請建立目錄以在本機儲存符號檔。

2. 使用下列語法設定 **_NT_SYMBOL_PATH** 環境變數或 VSPerfReport /SymbolPath 選項：

    **srv\\** * *LocalStore* **\*http://msdl.microsoft.com/download/symbols**

    其中 *LocalStore* 代表您建立的本機目錄路徑。

## <a name="specify-component-symbol-files"></a>指定元件符號檔
 針對要進行程式碼剖析之元件的 .*pdb* 檔，程式碼剖析工具會在其原始位置 (可能儲存於元件或包含程式碼剖析資料檔的資料夾中) 進行搜尋。 您可以加入一或多個路徑至 **_NT_SYMBOL_PATH** 或 **/SymbolPath** 選項，以指定其他要搜尋的位置。 請使用分號分隔路徑。

## <a name="example"></a>範例
 下列命令列會將 **_NT_SYMBOL_PATH** 環境變數設定為 Windows 符號伺服器，以及將本機目錄設定為 **C:\Symbols**。

 **set  _NT_SYMBOL_PATH=srv\*C:\symbols\*http://msdl.microsoft.com/download/symbols**

 下列 VSPerfReport 命令列會使用 **/SymbolPath** 選項將 *C:\Projects\Symbols* 目錄新增至搜尋路徑。

 **VSPerfReport**  *MyApp* **.exe /SymbolPath:C:\Projects\Symbols /summary:all**

---
title: 支援的程式碼變更 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C# language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C#], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: bb97c08b8673854e0fe0d0bbd64efbe038227c43
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477033"
---
# <a name="supported-code-changes-c"></a>支援的程式碼變更 (C++)
Visual C++ 的 [編輯後繼續] 可處理大多數的程式碼變更類型。 不過，有些變更無法在程式執行期間套用。 若要套用這些變更，您必須停止執行，並建置新版的程式碼。  
  
 如需在 Visual Studio 中使用 C++ 的 [編輯後繼續] 的相關資訊，請參閱 [Edit and Continue (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) 。  
  
##  <a name="BKMK_Unsupported_changes"></a> 不支援的變更  
 偵錯工作階段期間不能套用下列 C/C++ 變更：  
  
-   大部分全域或靜態資料的變更。  
  
-   變更從另一部電腦複製而來，而不是在本機上建置的可執行檔。  
  
-   變更會影響物件 (例如，類別的資料成員) 配置的資料類型。  
  
-   加入超過 64K 位元組的新程式碼或資料。  
  
-   在指令指標之前的某一點加入需要建構函式的變數。  
  
-   會影響需要執行階段初始化之程式碼的變更。  
  
-   在某些執行個體中加入例外狀況處理常式。  
  
-   變更資源檔。  
  
-   變更唯讀檔中的程式碼。  
  
-   變更沒有對應之 PDB 檔的程式碼。  
  
-   變更沒有目的檔的程式碼。  
  
 如果您進行上述其中一項變更，並嘗試套用程式碼變更，則 [ **輸出** ] 視窗中會出現錯誤或警告訊息。  
  
-   [編輯後繼續] 不會更新靜態程式庫。 如果您變更靜態程式庫，執行仍會使用舊版繼續進行，而且不會發出任何警告。  
  
##  <a name="BKMK_Unsupported_scenarios"></a> 不支援的情節  
 C/C++ 的 [編輯後繼續] 無法用於下列偵錯案例中：  
  
-   偵錯以 [/Zo (增強最佳化偵錯)](/cpp/build/reference/zo-enhance-optimized-debugging)編譯的原生應用程式  
  
-   在 Visual Studio 2015 Update 1，偵錯 UWP 應用程式或元件之前的 Visual Studio 版本。 從 Visual Studio 2015 Update 1 開始，您可以使用 編輯後繼續中 UWP c + + 應用程式和 DirectX 應用程式，因為它現在支援`/ZI`編譯器參數和`/bigobj`切換。 您也可以搭配以 `/FASTLINK` 參數。  
  
-   在 Windows 98 上偵錯。  
  
-   混合模式 (原生/Managed) 偵錯。  
  
-   Javascript 偵錯。  
  
-   SQL 偵錯  
  
-   對傾印檔偵錯。  
  
-   在未選取 [ **發生未處理的例外狀況時回溯呼叫堆疊** ] 選項的情況下，於發生未處理的例外狀況後編輯程式碼。  
  
-   使用 [附加至]  來進行應用程式偵錯，而不要選擇 [偵錯]  功能表上的 [啟動]  來執行應用程式。  
  
-   偵錯最佳化程式碼  
  
-   由於建置錯誤以致新版本建置失敗之後，對舊版程式碼進行偵錯。  
  
##  <a name="BKMK_Linking_limitations"></a> 連結的限制  
  
###  <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> 停用 [編輯後繼續] 的連結器選項  
 下列連結器選項停用 [編輯後繼續]：  
  
-   設定 **/OPT:REF**、 **/OPT:ICF**，或 **/INCREMENTAL:NO** 會停用 [編輯後繼續]，並且產生下列警告：  
  
     連結：警告 LNK4075：由於 /OPT 而忽略 /EDITANDCONTINUE  
  
     規格  
  
-   設定 **/ORDER**、 **/RELEASE**或 **/FORCE** ，會停用 [編輯後繼續] 並且產生這則警告：  
  
     連結：警告 LNK4075：由於 /option 而忽略 /INCREMENTAL  
  
     規格  
  
-   設定任何能夠防止建立程式資料庫 (.PDB) 檔的選項，即可停用 [編輯後繼續] 並且不顯示任何特定警告。  
  
###  <a name="BKMK_Auto_relinking_limitations"></a> 自動重新連結的限制  
 根據預設，[編輯後繼續] 會在偵錯工作階段結束後重新連結程式，建立最新的執行檔。  
  
 如果您不是在原來的組建位置上偵錯，[編輯後繼續] 無法重新連結您的程式。 會有一則訊息告訴您必須手動重建。  
  
 [編輯後繼續] 不重建靜態程式庫。 如果您使用 [編輯後繼續] 來變更靜態程式庫，則必須手動重建程式庫，再用它重新連結應用程式。  
  
 [編輯後繼續] 不會叫用自訂組建步驟。 如果您的程式使用自訂的建置步驟，您應當以手動方式重建，讓自訂的建置步驟能夠被叫用。 在那情況下，您可以在 [編輯後繼續] 之後停用重新連結，確保您會被提示以手動重建。  
  
 **若要在編輯後繼續後停用重新連結**  
  
1.  在 [ **偵錯** ] 功能表上選擇 [ **選項和設定**]。  
  
2.  在 [選項]  對話方塊的 [偵錯]  節點下，選取 [編輯後繼續]  節點。  
  
3.  清除 [ **偵錯後重新連結程式碼變更** ] 核取方塊。  
  
##  <a name="BKMK_Precompiled_Header_Limitations"></a> 先行編譯標頭的限制  
 根據預設，[編輯後繼續] 會在背景載入並處理預先編譯的標頭，以加速程式碼變更的處理。 載入預先編譯的標頭檔須配置實體記憶體，如果您是在一部 RAM 不足的電腦上進行編譯，這可能會是個問題。 您可以在偵錯時，使用 [Windows 工作管理員] 判斷可用的實體記憶體數量，來判斷這樣是否會發生問題。 如果此一數量大於預先編譯的標頭檔的大小，[編輯後繼續] 應該不會有問題。 如果數量小於您先行編譯的標頭大小，您可以防止 [編輯後繼續] 在背景中載入先行編譯的標頭。  
  
 **若要停用編輯後繼續的先行編譯標頭的背景載入**  
  
1.  在 [ **偵錯** ] 功能表上選擇 [ **選項和設定**]。  
  
2.  在 [選項]  對話方塊的 [偵錯]  節點下，選取 [編輯後繼續]  節點。  
  
3.  清除 [ **允許先行編譯** ] 核取方塊。  
  
##  <a name="BKMK_IDL_Attribute_Limitations"></a> IDL 屬性的限制  
 [編輯後繼續] 不會重新產生介面定義 (IDL) 檔， 所以您偵錯時並不會反映出 IDL 屬性的變更。 若要看到 IDL 屬性的變更結果，就必須停止偵錯並重建應用程式。 如果 IDL 屬性有所變更，[編輯後繼續] 並不會產生錯誤或警告。 如需詳細資訊，請參閱 [IDL 屬性](/cpp/windows/idl-attributes)。  
  
## <a name="see-also"></a>另請參閱  
 [Edit and Continue (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)
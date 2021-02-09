---
title: 診斷資料和系統產生的記錄檔
description: 瞭解 Visual Studio 系統產生的記錄檔、所收集的資料類型，以及如何使用它來修正問題及改善產品品質。
ms.custom: SEO-VS-2020
ms.date: 05/24/2018
ms.topic: conceptual
author: jillre
ms.author: michma
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a6df4a90d8ddb31db88bb91ff4e874cadd3c589
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894656"
---
# <a name="system-generated-logs-collected-by-visual-studio"></a>Visual Studio 所收集的系統產生記錄檔

Visual Studio 會透過 [Visual Studio 客戶經驗改進計畫](visual-studio-experience-improvement-program.md)收集系統產生的記錄檔來修正問題，並改善產品的品質。 本文提供我們所收集資料類型和如何使用它的一些資訊。 它也提供有關延伸模組作者如何避免意外洩漏個人或機密資訊的祕訣。

## <a name="types-of-collected-data"></a>收集的資料類型

Visual Studio 會收集系統產生的記錄檔，以尋找損毀、UI 無回應，以及高 CPU 或記憶體使用量。 我們也會收集在產品安裝或使用期間遇到之錯誤的相關資訊。 收集的資料會根據錯誤而異，而且可能包括堆疊追蹤、記憶體傾印，以及例外狀況資訊：

- 針對高 CPU 使用量和無回應，會收集相關 Visual Studio 執行緒的堆疊追蹤。

- 在某些執行緒的堆疊追蹤不足以判斷問題根本原因的情況下（例如當機、無回應或高記憶體使用量），我們會收集記憶體 *轉儲*。 傾印代表在發生錯誤時的處理序狀態。

- 針對非預期的錯誤情況，例如，嘗試寫入至磁碟上的檔案時發生例外狀況，我們會收集例外狀況的相關資訊。 資訊包括例外狀況的名稱、發生例外狀況之執行緒的堆疊追蹤、與例外狀況建立關聯的訊息，以及與特定例外狀況相關的其他資訊。

   下列收集資料範例會顯示例外狀況名稱、堆疊追蹤和例外狀況訊息：

   ```text
   "Reserved.DataModel.Fault.Exception.TypeString": "System.IO.IOException",
   "Reserved.DataModel.Fault.Exception.StackTrace": "System.IO.__Error.WinIOError(Int32,String)\r\n
   System.IO.FileStream.Init(String,FileMode,FileAccess,Int32,Boolean,FileShare,Int32,FileOptions,SECURITY_ATTRIBUTES,String,Boolean,Boolean,Boolean)\r\n
   System.IO.FileStream..ctor(String,FileMode,FileAccess,FileShare,Int32,FileOptions,String,Boolean,Boolean,Boolean)\r\nSystem.IO.StreamWriter.CreateFile(String,Boolean,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean,Encoding,Int32,Boolean)\r\n
   System.IO.StreamWriter..ctor(String,Boolean)\r\n
   System.IO.File.CreateText(String)\r\n
   Microsoft.VisualStudio.Setup.Services.FileSystem.CreateText(String,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.WriteChannelManifest(IChannelManifest,String,String)\r\n
   Microsoft.VisualStudio.Setup.Cache.ChannelManifestRepository.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.Cache.CacheManager.AddChannel(ChannelManifestPair,Boolean)\r\n
   Microsoft.VisualStudio.Setup.ChannelManager.\<UpdateAsync>d__37.MoveNext()\r\n”,
   "Reserved.DataModel.Fault.Exception.Message": " The process cannot access the file 'C:\\Users\\[UserName]\\AppData\\Local\\Microsoft\\VisualStudio\\Packages\\_Channels\\4CB340F5\\channelManifest.json' because it is being used by another process."
   ```

## <a name="how-we-use-system-generated-logs"></a>我們如何使用系統產生的記錄檔

判斷錯誤根本原因的工作流程，會視錯誤類型和其嚴重性而有所不同。

### <a name="error-classification"></a>錯誤分類

根據記錄檔，錯誤會分類並計算，以排列調查的優先順序。 例如，我們可能會發現「System.IO。 \_WinIOError "at" System.IO.FileStream.Init "在產品版本中發生500次 \<x> ，且在該版本中具有最高的發生率。 _Error

### <a name="work-items-for-tracking"></a>追蹤用的工作項目

對於個別已排列優先順序的錯誤，已建立工作項目並指派給工程師進行調查。 這些工作項目通常包含分類、優先順序和與錯誤類型相關的診斷資訊。 這項資訊衍生自已收集到之系統針對錯誤所產生的記錄檔。 例如，損毀的工作項目可能包含發生損毀處的堆疊追蹤。

### <a name="error-investigation"></a>錯誤調查

工程師會使用工作項目中可用的資訊來判斷錯誤的根本原因。 在某些情況下，他們需要比出現在工作項目中更多的資訊，在此情況下他們會參考已收集到的原始系統產生記錄檔。 例如，工程師可能會檢查記憶體傾印以了解產品損毀。

## <a name="tips-for-extension-authors"></a>延伸模組作者的祕訣

延伸模組作者應該限制個人資訊的曝光，方法是不以其模組、類型和方法的名義來使用個人或其他機密資訊。 如果損毀或發生類似的錯誤狀況並在堆疊上具有該代碼，則會收集該資訊成為系統產生的記錄檔的一部分。

## <a name="opt-out-of-data-collection"></a>選擇不使用資料收集

了解我們所收集的資料和其存取和保留之條件約束的用途之後，我們建議您針對 Visual Studio 和 Windows 使用預設的隱私權設定。 不過，您可以[選擇退出](../ide/visual-studio-experience-improvement-program.md#opt-in-or-out) Visual Studio 經驗改進計畫。 若要選擇退出所有計畫的系統產生記錄檔收集，請參閱 [Windows 10 中的診斷、意見反應與隱私權](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)。 選項可能會根據您所使用的 Windows 版本而異。

## <a name="see-also"></a>另請參閱

- [Visual Studio 客戶經驗改進計畫](visual-studio-experience-improvement-program.md)
- [Windows 10 中的診斷、意見反應與隱私權](https://privacy.microsoft.com/windows-10-feedback-diagnostics-and-privacy)
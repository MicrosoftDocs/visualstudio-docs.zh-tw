---
title: 疑難排解 Visual Studio 偵錯工具中的中斷點 |Microsoft 文件
ms.custom: ''
ms.date: 01/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d587809a9690e312e923ba184c9d90c38405a5d6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477101"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>疑難排解 Visual Studio 偵錯工具中的中斷點

## <a name="breakpoint-warnings"></a>中斷點警告

偵錯時，中斷點就會有兩個可能的視覺狀態： 實心的紅色圓圈和 （白色區域分布） 空心圓圈。 如果偵錯工具可以成功地在目標處理序中設定中斷點，它會保持實心的紅色圓圈。 如果中斷點是空心的圓形，已停用中斷點，或嘗試設定此中斷點時發生警告。 若要判斷的差異，將滑鼠停留在中斷點並查看是否有警告。

下列兩節則描述顯著的警告，以及如何加以修正。 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>「 此文件已不載入任何符號 」 

移至**模組**視窗 (**偵錯** > **Windows** > **模組**) 並檢查是否在模組載入。  
* 如果您的模組載入時，請檢查**符號狀態**欄，以查看是否已載入符號。 
  * 如果未載入符號，請檢查符號狀態來診斷問題。 從內容功能表中的模組上**模組**視窗中，按一下 **符號載入資訊...** 以查看偵錯工具尋找並嘗試載入符號的位置。 如需載入符號的詳細資訊，請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  * 如果已載入符號，這表示 PDB 不包含來源檔案的相關資訊。 以下是幾個可能的原因： 
    * 如果最近已新增您的來源檔案，請確認正在載入的模組最新版本。  
    * 您可建立使用已移除的 Pdb **/PDBSTRIPPED**連結器選項。 已移除的 Pdb 不包含原始程式檔資訊。 確認您使用完整的 PDB 和不等量的 PDB。  
    * PDB 檔案部分損毀。 請嘗試刪除檔案，並執行乾淨的組建，以查看是否有此模組的解析問題。 

* 如果未載入模組，請檢查下列命令來找出原因： 
  * 確認您正在偵錯正確的處理序。 
  * 請檢查您正在偵錯正確類型的程式碼。 您可以找出何種程式碼偵錯工具已設定為在偵錯**處理程序**視窗 (**偵錯** > **Windows**  >  **處理程序**)。 比方說，如果您嘗試偵錯 C# 程式碼，確認您偵錯工具已針對適當的.NET Framework 類型 (例如，Managed (v4\*) 與受管理 (v2\*/v3\*) 與受管理 (CoreCLR))。 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… 目前的原始碼是不同版本的內建...」 

如果原始程式檔已變更，且來源不再符合您要偵錯的程式碼，偵錯工具將不設定中斷點在程式碼中預設。 一般來說，此問題發生時變更的原始程式檔，而不重建的原始程式碼。 若要修正此問題，請重建專案。 如果專案已經最新狀態，雖然它不會認為建置系統，您可以強制重建藉由重新儲存原始程式檔或清理專案的建置輸出之前建置專案系統。 

在極少數的情況下，您可能想要偵錯而不相符的原始碼。 這可以讓人十分混淆的偵錯經驗會導致，因此請確定這是您要如何繼續。  

若要停用這些安全檢查，請執行下列其中一項： 
* 若要修改單一中斷點，將滑鼠停留在編輯器中的 [中斷點] 圖示，然後按一下設定 （齒輪） 圖示。 編輯器會加入 [查看] 視窗。 在 [查看] 視窗頂端沒有超連結，以指出中斷點的位置。 按一下此超連結可允許修改中斷點的位置，並檢查**允許原始程式碼與原始版本不同**。
* 若要修改此設定的所有中斷點，請移至**偵錯** > **選項和設定**。 在 [偵錯] / [一般]  頁面上，清除 [原始程式檔必須完全符合原始版本]  選項。 確定要重新啟用此選項，當您完成偵錯。 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>中斷點已成功設定 （不警告），但是未叫用 

本節提供資訊以解決問題，當偵錯工具沒有顯示任何警告 – 中斷點實心的紅色圓圈主動偵錯時，但不叫用中斷點。 

以下是要檢查的一些事項： 
1. 如果在多個處理序或多部電腦中，執行您的程式碼，請確定您正在偵錯正確的處理序或電腦。  
2. 確認您的程式碼正在執行。 其中一個簡便的方式測試這種情況是將呼叫加入`System.Diagnostics.Debugger.Break`(C# /VB) 或`__debugbreak`（c + +） 的程式碼行所在想要設定中斷點，然後重建您的專案。 
3. 如果您正在偵錯最佳化程式碼，請確定函式設定中斷點的位置不正在執行另一個函式內嵌。 `Debugger.Break`測試步驟，在上一個檢查可運作，以測試這種情況以及。 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>我刪除了中斷點，但再次啟動偵錯時繼續叫用此中斷點 

如果您刪除了中斷點，偵錯時，您可能會在的下次您啟動偵錯時遇到中斷點。 若要停止叫用此中斷點，請確定所有中斷點的執行個體都已從 [中斷點]  視窗中移除。  

---
title: 偵錯準備： Visual c + + 專案類型 |Microsoft 文件
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
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 64d49d799c0ec0b3845a262c248d2438572ecd5d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-preparation-visual-c-project-types"></a>偵錯準備：Visual C++ 專案類型
本節說明如何對 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 專案範本所建立的基本專案類型進行偵錯。  
  
 請注意，這些專案類型，建立 Dll，做為其輸出均已分組為[偵錯 DLL 專案](../debugger/debugging-dll-projects.md)因為它們共用通用的功能。  
  
##  <a name="BKMK_In_this_topic"></a>本主題內容  
 [建議的屬性設定](#BKMK_Recommended_Property_Settings)  
  
 [Win32 專案](#BKMK_Win32_Projects)  
  
-   [若要偵錯 C 或 c + + Win32 應用程式](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [若要手動設定偵錯組態](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Windows Form 應用程式 (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> 建議的屬性設定  
 在所有 Unmanaged 偵錯情況中，某些屬性必須以相同的方式設定。 下表顯示建議的屬性設定。 此處未列出的設定，可能會因不同的 Unmanaged 專案類型而異。 如需詳細資訊，請參閱[c + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>組態屬性&#124;C/c + +&#124;最佳化節點  
  
|屬性名稱|設定|  
|-------------------|-------------|  
|**Optimization**|設定為**已停用 (/ 0d)。** 最佳化程式碼較難偵錯，因為產生的指令不能直接對應到您的原始程式碼。 如果您發現程式含有僅出現在最佳化程式碼的錯誤，您可以啟動這個設定，但是請記住該程式碼所示**反組譯碼**視窗由最佳化原始程式碼所產生可能不符合您在來源中看到的內容windows。 其他功能 (例如逐步執行) 可能無法如預期般地執行。|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>組態屬性&#124;連結器&#124;偵錯 節點  
  
|屬性名稱|設定|  
|-------------------|-------------|  
|**產生偵錯資訊**|您應該一律將此選項設定為**是 (/debug)** 建立偵錯符號和偵錯所需的檔案。 當應用程式開始運作時，就可以將其設定為關閉。|  
  
 [本主題內容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Win32 專案  
 Win32 應用程式是以 C 或 C++ 撰寫的傳統 Windows 程式。 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中可以直接偵錯這種類型的應用程式。  
  
 Win32 應用程式包括 MFC 應用程式和 ATL 專案。 它們會使用 Windows API，也可能會使用 MFC 或 ATL，但是不會使用 Common Language Runtime (CLR)。 但是，它們能呼叫使用 CLR 的 Managed 程式碼。  
  
 下列程序說明在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 內偵錯 Win32 專案的方法。 另一個偵錯 Win32 應用程式的方法，是在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外部啟動應用程式，然後進行附加。 如需詳細資訊，請參閱[附加至執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> 若要偵錯 C 或 c + + Win32 應用程式  
  
1.  在 Visual Studio 中開啟專案。  
  
2.  在**偵錯**功能表上，選擇**啟動**。  
  
3.  使用中討論的技術進行偵錯[偵錯工具基本概念](../debugger/debugger-basics.md)。  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> 若要手動設定偵錯組態  
  
1.  在**檢視**功能表上，按一下 **屬性頁**。  
  
2.  按一下**組態屬性**節點以開啟它，如果不存在  
  
3.  選取**一般**，並將值的**輸出**資料列於**偵錯**。  
  
4.  開啟**C/c + +** 節點，然後選取**一般**。  
  
     在**偵錯**您指定偵錯資訊由編譯器產生類型的資料列。 您可能會選擇的值包括**程式資料庫 (/Zi)** 或**編輯後繼續 (/ZI) 的程式資料庫**。  
  
5.  選取**最佳化**，然後在**最佳化**列中選取**已停用 (/ 0d)** 從下拉式清單。  
  
     最佳化程式碼較難偵錯，因為產生的指令不能直接對應到您的原始程式碼。 如果您發現程式含有僅出現在最佳化程式碼中的錯誤，您可以啟動這個設定，但是請記住，顯示在 [反組譯碼] 視窗裡的程式碼是由最佳化原始程式碼所產生，可能無法對應至您在原始程式碼視窗所看到的內容。 逐步執行之類的功能，可能無法正確顯示中斷點和執行點。  
  
6.  開啟**連結器**節點，然後選取**偵錯**。 在第一個**產生**列中選取**是 (/debug)** 從下拉式清單。 進行偵錯時，一律要設定這個選項。  
  
 如需詳細資訊，請參閱[c + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)。  
  
 [本主題內容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows Form 應用程式 (.NET)  
 **Windows Forms 應用程式 (.NET)** 範本會建立[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]Windows Forms 應用程式。 如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中偵錯這種類型的應用程式，與偵錯 Managed Windows Form 應用程式類似。  
  
 當您以專案範本建立 Windows Form 專案時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動建立偵錯和發行組態所需要的設定。 如果有必要，您可以變更這些設定在**\<專案名稱 > 屬性頁** 對話方塊。 如需詳細資訊，請參閱[偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。  
  
 如需詳細資訊，請參閱[c + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)。  
  
 偵錯 Windows Form 應用程式的另一種方法，是在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 外啟動應用程式並且附加於其上。 如需詳細資訊，請參閱[將附加至正在執行的程式或多個程式](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。  
  
 [本主題內容](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具基礎](../debugger/debugger-basics.md)   
 [C + + 偵錯組態的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [將附加至正在執行的程式或多個程式](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)   
 [如何： 建立 Windows 應用程式專案](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)
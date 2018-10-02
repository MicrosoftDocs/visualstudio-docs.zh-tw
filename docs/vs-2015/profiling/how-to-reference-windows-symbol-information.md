---
title: 如何：參考 Windows 符號資訊 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 385b9e4511c44c02a358eb88471cd8369971ed1c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499853"
---
# <a name="how-to-reference-windows-symbol-information"></a>如何：參考 Windows 符號資訊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 參考 Windows 符號資訊](https://docs.microsoft.com/visualstudio/profiling/how-to-reference-windows-symbol-information)。  
  
Visual Studio 程式碼剖析工具會使用符號 (.pdb) 檔案來解析符號名稱，例如程式二進位檔案中的函式名稱。 您可以依照下列步驟進行，以為本機電腦上的 Windows 版本自動下載並更新正確的 .pdb 檔案。  
  
> [!NOTE]
>  此設定不會影響現有的報告。 只有在指定符號伺服器之後所建立的報告會含有符號資訊。  
  
 如需詳細資訊，請參閱[指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。  
  
### <a name="to-use-the-microsoft-symbol-server"></a>使用 Microsoft 符號伺服器  
  
1.  建立要包含符號檔案資訊的資料夾，例如 C:\SymbolCache。  
  
2.  在 [ **工具** ] 功能表上按一下 [ **選項**]。  
  
     [ **選項** ] 對話方塊隨即出現。  
  
3.  展開 [偵錯] 樹狀結構，然後按一下 [符號]。  
  
4.  在 [符號檔 (.pdb) 位置] 中，選取 [Microsoft 符號伺服器]  
  
5.  在 [從符號伺服器將符號快取至此目錄] 中，輸入在步驟 1 建立的資料夾路徑，例如︰  
  
     **C:\SymbolCache**  
  
     您也可以按一下省略符號按鈕 (**...**)，然後從 [瀏覽資料夾] 對話方塊選取一個目錄。  
  
## <a name="see-also"></a>另請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)   
 [如何：序列化符號資訊](../profiling/how-to-serialize-symbol-information.md)




---
title: HOW TO：參考 Windows 符號資訊 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91b5c90b2451780458982ba73a0e04672fa2e507
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422832"
---
# <a name="how-to-reference-windows-symbol-information"></a>HOW TO：參考 Windows 符號資訊
Visual Studio 程式碼剖析工具會使用符號 (.*pdb*) 檔案來解析符號名稱，例如程式二進位檔案中的函式名稱。 您可以遵循下列步驟來自動下載並更新本機電腦上之 Windows 版本的正確 .*pdb* 檔案。

> [!NOTE]
> 此設定不會影響現有的報告。 只有在指定符號伺服器之後所建立的報告會含有符號資訊。

 如需詳細資訊，請參閱[指定符號 (.*pdb*) 和原始程式檔 ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。

### <a name="to-use-the-microsoft-symbol-server"></a>使用 Microsoft 符號伺服器

1. 建立要包含符號檔案資訊的資料夾，例如 C:\SymbolCache。

2. 在 [ **工具** ] 功能表上按一下 [ **選項**]。

     [ **選項** ] 對話方塊隨即出現。

3. 展開 [偵錯] 樹狀結構，然後按一下 [符號]。

4. 在 [符號檔 (.pdb) 位置] 中，選取 [Microsoft 符號伺服器]

5. 在 [從符號伺服器將符號快取至此目錄] 中，輸入在步驟 1 建立的資料夾路徑，例如︰

     **C:\SymbolCache**

     您也可以按一下省略符號按鈕 (**...**)，然後從 [瀏覽資料夾] 對話方塊選取一個目錄。

## <a name="see-also"></a>另請參閱
- [設定效能工作階段](../profiling/configuring-performance-sessions.md)
- [如何：序列化符號資訊](../profiling/how-to-serialize-symbol-information.md)
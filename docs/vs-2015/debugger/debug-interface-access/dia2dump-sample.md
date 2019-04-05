---
title: Dia2dump 範例 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd52c635d5ade1bef73176601d6957ba5859723b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944381"
---
# <a name="dia2dump-sample"></a>Dia2dump 範例
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dia2dump 範例隨附於 Visual Studio，並包含 Dia2dump.cpp 原始程式檔。 已編譯的可執行檔會從命令列執行，並顯示整個程式資料庫 (.pdb) 檔案的內容。  
  
### <a name="to-install-the-sample"></a>若要安裝範例  
  
1.  請確認您的系統符合 Visual Studio 安裝程式起始頁中所述的所有設定需求。  
  
2.  安裝 Visual Studio，並遵循內含範例的所有設定和安裝指示。  
  
#### <a name="to-build-the-sample"></a>若要建置範例  
  
1.  在 Visual Studio 中開啟 Dia2dump.sln 檔案。 (如有必要，Visual Studio 會先協助您升級 Dia2dump 專案。）  
  
2.  在 [專案屬性頁中**C/c + +** &#124; **一般** &#124; **其他 Include 目錄**] 屬性，指定`..\DIA SDK\include`目錄。 這可確保編譯器可以找到 dia2.h 檔案。  
  
3.  在 [建置] 功能表上，按一下 [重建方案]。  
  
4.  關閉 Visual Studio。  
  
#### <a name="to-run-the-sample"></a>若要執行範例  
  
1.  開啟命令提示字元並輸入下列命令：  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Dia2dump.cpp 原始程式檔](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [如何：不成功的 Visual Studio 專案升級疑難排解](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)

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
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197597"
---
# <a name="dia2dump-sample"></a>Dia2dump 範例
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dia2dump 範例會隨 Visual Studio 一起安裝，並包含 Dia2dump .cpp 來源檔案。 從命令列執行已編譯的可執行檔，並將整個程式資料庫的內容顯示 ( .pdb) 檔。  
  
### <a name="to-install-the-sample"></a>安裝範例  
  
1. 確認您的系統符合 Visual Studio 安裝程式起始頁中所述的所有安裝需求。  
  
2. 安裝 Visual Studio，並遵循內含範例的所有安裝和安裝指示。  
  
#### <a name="to-build-the-sample"></a>若要建置範例  
  
1. 在 Visual Studio 中開啟 Dia2dump .sln 檔案。  (如有必要，Visual Studio 會先協助您升級 Dia2dump 專案。 )   
  
2. 在專案屬性頁的 [ **C/c + +** ] &#124; **一般** &#124; **其他 Include 目錄** ] 屬性中，指定 `..\DIA SDK\include` 目錄。 這可保證編譯器可以找到 dia2 .h 檔案。  
  
3. 在 [建置]**** 功能表上，按一下 [重建方案]****。  
  
4. 關閉 Visual Studio。  
  
#### <a name="to-run-the-sample"></a>執行範例  
  
1. 開啟命令提示字元並輸入下列內容：  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [Dia2dump .cpp 來源檔案](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [如何：不成功的 Visual Studio 專案升級疑難排解](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)

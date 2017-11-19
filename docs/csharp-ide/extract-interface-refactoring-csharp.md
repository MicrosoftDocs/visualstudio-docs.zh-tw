---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-interface
title: "擷取介面重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4ed81f6f0fbcc2e72fd57d7706b051dcdf7bea75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="extract-interface-refactoring-c"></a>擷取介面重構 (C#)
擷取介面 是提供簡單的方式，使用來自現有的類別、 結構或介面的成員建立的新介面重構作業。  
  
 當數個用戶端使用的類別、 結構或介面成員相同的子集或多個類別、 結構或介面共有的成員子集的它可具體表現介面中的成員子集。 如需有關使用介面的詳細資訊，請參閱[介面](/dotnet/csharp/programming-guide/interfaces/index)。  
  
 擷取介面會產生新的檔案中的介面，並將游標置於新的檔案的開頭。 您可以指定要擷取至新的介面、 新的介面，名稱和產生的檔案使用的名稱的成員**擷取介面** 對話方塊。  
  
### <a name="to-use-extract-interface"></a>若要使用 擷取介面  
  
1.  建立名為主控台應用程式`ExtractInterface`，然後取代`Program`為下列程式碼  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  將游標放置在`MethodB`，然後按一下**擷取介面**上**重構**功能表。  
  
     **擷取介面** 對話方塊隨即出現。  
  
     您也可以輸入鍵盤快速鍵 CTRL + R、 我顯示**擷取介面** 對話方塊。  
  
     您也可以以滑鼠右鍵按一下滑鼠，指向 **重構**，然後按一下 **擷取介面**顯示**擷取介面** 對話方塊。  
  
3.  按一下**選取所有**。  
  
4.  按一下 [確定]。  
  
     您會看到新的檔案、 IProtoA.cs 和下列程式碼：  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>備註  
 將游標放在類別、 結構或介面，其中包含您想要擷取的成員時，才可存取此功能。 在這個位置中的資料指標時，叫用 擷取介面重構作業。  
  
 當您叫用類別或結構上的 擷取介面時，基底和介面清單會修改成包含新的介面名稱。 當您叫用在介面上的 擷取介面時，則不會修改基底和介面清單。  
  
## <a name="see-also"></a>另請參閱  
 [重構 (C#)](refactoring-csharp.md)
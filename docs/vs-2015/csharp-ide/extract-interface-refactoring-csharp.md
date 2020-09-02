---
title: " (c # ) 解壓縮介面重構 |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667556"
---
# <a name="extract-interface-refactoring-c"></a>擷取介面重構 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

「解壓縮介面」是一項重構作業，可讓您輕鬆地使用源自現有類別、結構或介面的成員來建立新的介面。

 當數個用戶端使用來自類別、結構或介面的相同成員子集，或是當多個類別、結構或介面具有共同成員的子集時，體現介面中的成員子集可能會很有用。 如需使用介面的詳細資訊，請參閱 [介面](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)。

 「解壓縮介面」會在新檔案中產生介面，並將游標置於新檔案的開頭。 您可以使用 [ **解壓縮介面** ] 對話方塊來指定要將哪些成員解壓縮至新介面、新介面的名稱，以及所產生之檔案的名稱。

### <a name="to-use-extract-interface"></a>使用解壓縮介面

1. 建立名為的主控台應用程式 `ExtractInterface` ，然後 `Program` 以下列程式碼取代

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. 將游標放在中 `MethodB` ，然後按一下 [**重構**] 功能表上的 [**解壓縮介面**]。

     [ **解壓縮介面** ] 對話方塊隨即出現。

     您也可以輸入鍵盤快速鍵 CTRL + R，以顯示 [ **解壓縮介面** ] 對話方塊。

     您也可以用滑鼠右鍵按一下滑鼠，指向 [ **重構**]，然後按一下 [ **解壓縮介面** ]，以顯示 [ **解壓縮介面** ] 對話方塊。

3. 按一下 [ **全選**]。

4. 按一下 [確定]  。

     您會看到新的檔案、IProtoA.cs 和下列程式碼：

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
 只有當資料指標位於包含您想要解壓縮之成員的類別、結構或介面中時，才可存取這項功能。 當游標位於這個位置時，會叫用「解壓縮介面」重構作業。

 當您在類別或結構上叫用「解壓縮介面」時，基底和介面清單會經過修改，以包含新的介面名稱。 當您在介面上叫用 [解壓縮介面] 時，不會修改基底和介面清單。

## <a name="see-also"></a>另請參閱
 [重構 (C#)](../csharp-ide/refactoring-csharp.md)
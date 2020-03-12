---
title: 在 Visual Studio 訂用帳戶中尋找及索取產品金鑰 |Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/09/2020
ms.topic: conceptual
description: 了解如何在 Visual Studio 訂用帳戶中尋找、索取及匯出產品金鑰
ms.openlocfilehash: 984a89f5085867ea7b23735d05d0e22ef51dcfdb
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937498"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>在 Visual Studio 訂用帳戶中尋找及索取產品金鑰
本文說明如何從 https://my.visualstudio.com/productkeys 尋找、索取及匯出產品金鑰。  如需使用金鑰、零售和大量授權版本的金鑰來啟用產品，以及每日產品金鑰索取限制的詳細資訊，請瀏覽[產品金鑰概觀](product-keys.md)。

## <a name="locating-and-claiming-product-keys"></a>尋找和索取產品金鑰
您必須登入 Visual Studio 訂用帳戶才能檢視您的產品金鑰。 在 [[下載]](https://my.visualstudio.com/downloads) 頁面選取特定產品的藍色 [取得金鑰] 連結，即可找到個別的產品金鑰，如下所示。  [產品金鑰](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs)頁面也彙總提供所有金鑰。 如果單一產品存在多組金鑰，下載的 [備註] 欄上就會顯示附註，協助您識別應該使用的金鑰。
> [!div class="mx-imgBorder"]
> ![從下載頁面取得金鑰](_img/product-keys/download-get-key.png)

部分產品將該產品的多重版本包裝為單一下載。 在這種情況下，輸入的產品金鑰會決定要安裝的產品版本。
有的金鑰會自動提供，例如「靜態」金鑰，因為它不需要啟用，所以您可以不限次數地使用。 有的金鑰則必須選取產品的 [取得金鑰] 連結才能領取。

根據產品提供各種金鑰類型。

### <a name="product-key-types"></a>產品金鑰類型

|    索引鍵類型           |    描述                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    不適用                    |    安裝這個產品並不需要任何金鑰。                                                       |
|    零售                     |    零售金鑰允許多次啟用，並且用於產品的零售版本。 在許多情況下，每一個金鑰可允許啟用產品 10 次，不過通常同一部機器可以允許啟用更多次。                                                       |
|    多次啟用        |    多次啟用金鑰 (MAK) 可讓您使用相同的金鑰啟用某產品的多重安裝。 MAK 一般是與產品的大量授權版本搭配使用。 每份訂用帳戶通常只提供一組 MAK 金鑰。    |
|    靜態啟用金鑰    |    靜態啟用金鑰是針對不需要啟用的產品而提供。 可以不限次數用於安裝。                                                                                                                  |
|    自訂金鑰                 |    自訂金鑰提供特殊動作或資訊來啟用或安裝產品。                                                                                                                                                                |
|    VA 1.0                     |    這些是多重啟用金鑰，與 MAK 類似。                                                                                                                                                                                                 |
|    OEM 金鑰                    |    這些是原始設備製造商金鑰，允許多次啟用。                                                                                                                                                                       |
|    DreamSpark 零售金鑰    |    這些零售金鑰適用於 DreamSpark，允許單次啟用。 DreamSpark 零售金鑰是以批次方式核發，而且主要是供學生取用。                                                                                     |
|    DreamSpark 實驗室金鑰         |    這些實驗室用金鑰適用於 DreamSpark 方案，允許多次啟用。 DreamSpark 實驗室金鑰是供大學電腦室環境使用。                                                                                       |
|    DreamSpark MAK 金鑰         |    這些是針對 DreamSpark 方案客戶所提供的 MAK 金鑰。                                                                                                                                                                                                  |
|

您可以在產品的下載頁面索取金鑰，或在[產品金鑰](https://my.visualstudio.com/productkeys)頁面搜尋所需金鑰。

### <a name="claiming-product-keys"></a>索取產品金鑰
只有訂用帳戶為使用中的訂閱者可以下載產品及索取產品金鑰。  您可以在訂用帳戶作用中時，從[產品金鑰](https://my.visualstudio.com/productkeys)頁面匯出領取的金鑰。

索取產品金鑰：
1. 登入 Visual Studio 訂用帳戶。  您必須登入才能下載產品或索取產品金鑰。
2. 按一下 [[產品金鑰]](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) 索引標籤。
3. 產品金鑰會依產品名稱的字母順序列出。  您可以向下捲動至所需產品的名稱，或使用頁面頂端的搜尋列搜尋產品。
> [!div class="mx-imgBorder"]
> ![搜尋產品金鑰](_img/product-keys/search-keys.png)
   
在此範例中，我們使用了搜尋列來尋找 Visual Studio Enterprise 2019 的產品金鑰。
您會看到列出數個版本。  已針對 Visual Studio Enterprise 2019 16.0 版和 16.1 版各索取一個金鑰。  這兩個版本仍可使用不同類型的其他金鑰。 請注意，您可以在 [備註] 欄中簡短註記已領取的金鑰。  這個項目可以和 [已領取] 欄中的日期搭配使用，追蹤已領取的金鑰。  例如，當您使用金鑰啟用產品安裝時，您可能會寫下它。

### <a name="exporting-your-claimed-keys"></a>匯出已領取的金鑰
您可以匯出所有已領取金鑰的清單，以及許多自動標示為您「已領取」的靜態和其他金鑰選項。

> [!IMPORTANT]
> 如果訂用帳戶到期，您就不能再索取新的金鑰或匯出已領取的金鑰。

若要匯出金鑰，按一下 [產品金鑰] 頁面最右邊的 [匯出所有金鑰] 連結即可。  即會建立標題為 KeysExport.xml 的 .xml 檔案，而您可以選擇開啟或儲存檔案。  您必須使用可以處理 .xml 檔案的應用程式開啟檔案。  例如，您可以使用 Excel 將檔案開啟為唯讀活頁簿。

## <a name="see-also"></a>另請參閱
- [Visual Studio 檔](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 檔](https://docs.microsoft.com/azure/devops/)
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Microsoft 365 檔](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>後續步驟
當您準備好下載軟體並使用金鑰時，請前往 https://my.visualstudio.com/downloads 。  如需下載軟體的詳細資訊，請參閱[下載概觀](download-software.md)。
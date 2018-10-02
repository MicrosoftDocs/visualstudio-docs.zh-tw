---
title: 如何： 管理專案中的本機資料檔案 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.LocalConnectionConverter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- mdf files
- local data
- .mdb files
- .mdf files
- data [Visual Studio], local
- mdb files
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b63a90a354935300c705c0bf96ae307e0468b4f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491241"
---
# <a name="how-to-manage-local-data-files-in-your-project"></a>如何：管理專案中的本機資料檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本機資料庫檔案可以包含為專案中的檔案。 第一次您連接到本機資料庫檔案，您可以選擇在專案中建立複本，或連接到現有的檔案，在目前的位置。 如果您連接到現有的檔案，則會將它維持在其原始位置。 如果您選擇將檔案複製到您的專案，Visual Studio 會建立一份，將它新增至您的專案，並修改指向要複製的連接。 此外，也會修改其他連線，例如伺服器總管 中。  
  
 屬性的預設設定取決於您使用的資料庫檔案的類型。 行為**複製到輸出目錄**屬性不適用於 Web 或 c + + 專案。  
  
 在開發期間，您可能想要在資料庫上檢視您的程式碼的效果，而不需要進行這些變更永久。 您可以這麼做的設定**複製到輸出目錄**屬性設為 true 的檔案。 專案組建，或按 f5 鍵，每次檔案會複製到 bin 資料夾，而該檔案中，不到您的專案根資料夾中的檔案進行變更。 只有在您藉由編輯資料庫結構描述或資料時，才變更專案根資料夾中的資料庫檔案**伺服器總管**，**資料庫總管**或其他工具視窗。  
  
 下表描述的設定**複製到輸出目錄**屬性。  
  
|設定|行為|  
|-------------|--------------|  
|**有更新時才複製**（.sdf 檔的預設值）|資料庫檔案從專案目錄複製到**bin**建置專案的目錄的第一個時間。 每次建置專案時，**修改日期**比較檔案的屬性。 如果專案資料夾中的檔案新時，它會複製到**bin**資料夾，取代目前的檔案。 如果中的檔案**bin**資料夾較新，便會複製任何檔案。 這項設定保存在執行期間，資料所做的變更，這表示，每次您執行您的應用程式，並將變更儲存至資料時，會看見這些變更的下次您執行應用程式。 **注意：** 我們不建議用於.mdb 或.mdf 檔案的這個選項。 即使資料會不進行任何變更，可以變更資料庫檔案。 只要開啟 資料檔案上的連線 (比方說，是藉由展開**資料表**中的節點**伺服器總管**) 可以將它標示為更新版本。|  
|**永遠複製**（.mdf 和.mdb 檔案的預設值）|資料庫檔案是從專案目錄複製到 /bin 目錄每次建置您的應用程式。 因此，如果您建置應用程式，並將變更儲存到 /bin 目錄中的檔案，這些變更會覆寫原始的檔案複製到 /bin 目錄下一次。|  
|**不要複製**|檔案永遠不會複製或覆寫專案系統。 如果您必須手動複製檔案從專案目錄到輸出目錄使用這項設定。|  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-respond-to-the-local-database-file-dialog-box"></a>若要回應本機資料庫檔案對話方塊  
  
-   按一下 **是**如果您想要 Visual Studio 將資料庫檔案複製到您的專案，並修改連接以指向您的專案中的複本。 如需有關使用您的專案中的資料庫檔案的詳細資訊，請參閱[本機資料概觀](../data-tools/local-data-overview.md)。  
  
-   按一下  **No**若不想讓 Visual Studio 將資料庫檔案複製到您的專案。 相反地，在原始位置中的檔案和資料庫檔案的連接點不會加入做為檔案至專案。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 連接至本機資料庫檔案 (Windows Form) 中的資料](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [連接至 Access 資料庫中的資料 (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)
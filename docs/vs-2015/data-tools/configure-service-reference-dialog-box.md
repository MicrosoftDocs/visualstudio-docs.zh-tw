---
title: '[設定服務參考] 對話方塊 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac8f4cf619bbdd007bb7aa570f549ae3c0b50e86
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651105"
---
# <a name="configure-service-reference-dialog-box"></a>設定服務參考對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[**設定服務參考**] 對話方塊可讓您設定 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] 服務的行為。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱在 Visual Studio 中自訂開發設定 [Walkthrough: Calling Code in an VSTO Add-in from VBA](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

 若要存取 [設定服務參考] 對話方塊，請以滑鼠右鍵按一下 [方案總管] 中的服務參考，然後選擇 [設定服務參考]。 您也可以按一下 [新增服務參考對話方塊] 中的 [進階] 按鈕來存取這個對話方塊。

## <a name="task-list"></a>工作清單

- 若要變更裝載 WCF 服務的位址，請在 [位址] 欄位中輸入新位址。

- 若要變更 WCF 用戶端中的類別存取層級，請在 [產生的類別存取層級] 清單中選取存取層級關鍵字。

- 若要以非同步方式呼叫 WCF 服務的方法，請選取 [產生非同步作業] 核取方塊。

- 若要產生 WCF 用戶端的訊息合約類型，請選取 [總是產生訊息合約] 核取方塊。

- 若要指定 WCF 用戶端的清單或字典集合類型，請從 [集合類型] 和 [字典集合類型] 清單中選取類型。

- 若要停用類型共用，請清除 [重複使用參考組件中的類型] 核取方塊。 若要針對參考組件的子集啟用類型共用，請選取 [重複使用參考組件中的類型] 核取方塊，然後選取 [重複使用指定的參考組件中的類型]，再從 [參考組件清單] 中選取所需的參考。

## <a name="uielement-list"></a>UIElement 清單
 **位址**用來更新服務參考在其中尋找服務的網址。 例如在開發期間，可能會在開發伺服器上裝載服務，稍後再將服務移至實際伺服器，並強迫變更位址。

> [!NOTE]
> 從 [新增服務參考對話方塊] 顯示 [設定服務參考] 對話方塊時，無法使用位址項目。

 **產生的類別的存取層級**決定 WCF 用戶端類別的程式碼存取層級。

> [!NOTE]
> 針對網站專案，這個選項一律會設為 `Public`，而且無法變更。 如需詳細資訊，請參閱針對[服務參考進行疑難排解](../data-tools/troubleshooting-service-references.md)。

 **產生非同步作業**決定要同步（預設）或非同步呼叫 WCF 服務方法。

 **產生以工作為基礎的作業**撰寫非同步程式碼時，此選項可讓您利用 .Net 4 引進的工作平行程式庫（TPL）。 請參閱工作[平行程式庫（TPL）](https://msdn.microsoft.com/library/dd460717.aspx)。

 **一律產生訊息合約**判斷是否會針對 WCF 用戶端產生訊息合約類型。 如需訊息合約的詳細資訊，請參閱[使用訊息合約](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249)。

 **集合類型**指定 WCF 用戶端的清單集合類型。 預設類型為 <xref:System.Array>。

 **字典集合類型**指定 WCF 用戶端的字典集合類型。 預設類型為 <xref:System.Collections.Generic.Dictionary%602>。

 **重複使用參考元件中的類型**判斷當加入或更新服務時，WCF 用戶端是否會嘗試重複使用已存在於參考元件中的，而不是產生新的類型。 預設會核取這個選項。

 **重複使用所有參考元件中的類型**選取時，會盡可能重複使用**參考元件清單**中的所有類型。 根據預設，這個選項是選取的。

 **重複使用指定的參考元件中的類型**選取時，只會重複使用 [**參考的元件] 清單**中選取的類型。

 **參考的元件清單**包含專案或網站之參考元件的清單。 選取 [**重複使用指定的參考元件中的類型**] 時，可以選取或清除個別元件。

 **新增 Web 參考**顯示 [[鋼筆：加入 Web 參考] 對話方塊](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)。

> [!NOTE]
> 只有針對以 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 版為目標的專案，才應使用這個選項。

> [!NOTE]
> 只有當 [**設定服務參考**] 對話方塊是從 [**加入服務參考] 對話方塊**顯示時，才可以使用 [**加入 Web 參考**] 按鈕。

## <a name="see-also"></a>請參閱
 [如何：加入、更新或移除服務參考](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)[如何：將參考加入至 Web 服務](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168) [Windows Communication Foundation 服務和 WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)

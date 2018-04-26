---
title: 設定服務參考對話方塊
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: abdb65b32f5f660257ecdc4d94fd9fcc387686f5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="configure-service-reference-dialog-box"></a>設定服務參考對話方塊

**設定服務參考**對話方塊可讓您設定 Windows Communication Foundation (WCF) 服務的行為。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

若要存取**設定服務參考**中參考的對話方塊中，以滑鼠右鍵按一下服務**方案總管 中**選擇**設定服務參考**。 您也可以存取對話方塊中，依序按一下**進階**按鈕**加入服務參考對話方塊**。

## <a name="task-list"></a>工作清單

- 若要變更裝載 WCF 服務的位址，請輸入中的新位址**位址**欄位。

- 若要變更在 WCF 用戶端類別的存取層級，選取存取層級關鍵字**存取產生的類別層級**清單。

- 若要以非同步方式呼叫 WCF 服務的方法，請選取**產生非同步作業**核取方塊。

- 若要在 WCF 用戶端產生訊息合約型別，請選取**總是產生訊息合約**核取方塊。

- 若要指定 WCF 用戶端的清單或字典集合類型，請選取 從型別**集合型別**和**字典集合型別**列出。

- 若要停用類型共用，請清除**重複使用參考組件中的型別**核取方塊。 若要啟用類型共用參考的組件的子集，請選取**重複使用參考組件中的型別**核取方塊，選取**重複使用指定參考的組件中的型別**，並選取所需在參考**參考組件清單**。

## <a name="uielement-list"></a>UIElement 清單

 **地址**

 用於更新網址，服務參考會在這個網址查詢服務。 例如在開發期間，可能會在開發伺服器上裝載服務，稍後再將服務移至實際伺服器，並強迫變更位址。

> [!NOTE]
> Address 項目時，不使用**設定服務參考**對話方塊會顯示從**加入服務參考對話方塊**。

 **產生的類別存取層級**

 判斷 WCF 用戶端類別的程式碼存取層級。

> [!NOTE]
> 針對網站專案，這個選項一律會設為 `Public`，而且無法變更。 如需詳細資訊，請參閱[疑難排解服務參考](../data-tools/troubleshooting-service-references.md)。

 **產生非同步作業**

 判斷將以同步方式 (預設) 或非同步方式呼叫 WCF 服務方法。

 **產生以工作為基礎的作業**

 撰寫非同步程式碼時，這個選項可讓您利用 .Net 4 所引進的工作平行程式庫 (TPL)。 請參閱[工作平行程式庫 (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)。

 **總是產生訊息合約**

 判斷是否會產生 WCF 用戶端的訊息合約類型。 如需訊息合約的詳細資訊，請參閱[使用訊息合約](/dotnet/framework/wcf/feature-details/using-message-contracts)。

 **集合型別**

 指定 WCF 用戶端的清單集合類型。 預設類型為 <xref:System.Array>。

 **字典集合類型**

 指定 WCF 用戶端的字典集合類型。 預設類型為 <xref:System.Collections.Generic.Dictionary%602>。

 **重複使用參考組件中的型別**

 判斷在加入或更新服務時，WCF 用戶端是否會嘗試重複使用參考組件中已存在的類型，而不是產生新類型。 預設會核取這個選項。

 **重複使用所有參考的組件中的型別**

 選取時中的所有類型**參考組件清單**將盡可能重複使用。 根據預設，這個選項是選取的。

 **重複使用指定參考的組件中的型別**

 選取時，只有在所選的類型**參考組件清單**會重複使用。

 **參考組件清單**

 包含專案或網站的參考組件清單。 當**重複使用指定參考的組件中的型別**選取時，可以選取或清除個別組件。

 **加入 Web 參考**

 顯示 [加入 Web 參考] 對話方塊。

> [!NOTE]
> 只有針對以 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 版為目標的專案，才應使用這個選項。

> [!NOTE]
> **加入 Web 參考**按鈕是只有**設定服務參考**對話方塊會顯示從**加入服務參考對話方塊**。

## <a name="see-also"></a>另請參閱

- [如何： 將參考加入至 Web 服務](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/configure-service-reference-dialog-box.md)
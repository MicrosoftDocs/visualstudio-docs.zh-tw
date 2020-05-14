---
title: 微軟視窗虛擬桌面優勢在可視化工作室訂閱 |微軟文件
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: 瞭解如何透過視覺化工作室訂閱利用 Microsoft Windows 虛擬桌面
ms.openlocfilehash: 87911b1b7b6eb63eb85b64515d5d24755e4656e6
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649739"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>在訂閱中存取 Windows 虛擬桌面 
Visual Studio 訂閱者現在能夠將其 Azure 開發/測試單個配額用於 Microsoft Windows 虛擬桌面服務。  
Windows 虛擬桌面是一種在雲中運行的綜合性桌面和應用虛擬化服務。 它是唯一提供簡化管理、多會話 Windows 10、Office 365 專業版優化和支援遠端桌面服務 (RDS) 環境的虛擬桌面基礎架構 (VDI)。 在幾分鐘內在 Azure 上部署和擴展 Windows 桌面和應用,並獲得內置的安全性和合規性功能。
以下是您在 Azure 上執行 Windows 虛擬桌面時可以執行的作業：
- 設定多工作階段的 Windows 10 部署，以提供具有延展性的完整 Windows 10
- 將 Office 365 ProPlus 虛擬化，並使其最佳化以在多使用者的虛擬案例中執行
- 提供具有免費擴充安全性更新的 Windows 7 虛擬桌面
- 將您現有的遠端桌面服務 (RDS) 和 Windows Server 桌面和應用程式帶到任何電腦
- 將桌面和應用程式虛擬化
- 使用統一的管理體驗管理 Windows 10、Windows 伺服器和 Windows 7 桌面和應用 有關 Windows 虛擬桌面可以做什麼的詳細資訊,請觀看[介紹性影片](https://docs.microsoft.com/azure/virtual-desktop/overview)。

## <a name="use-windows-virtual-desktop-with-azure"></a>將 Windows 虛擬桌面與 Azure 一起使用 
Visual Studio 訂閱者現在有多種使用 Azure 訂閱來支付 Windows 虛擬桌面服務的方法:
- [Azure 開發人員測試單個積分](vs-azure.md)。  作為訂閱的一部分,接收 Azure DevTest 單個配額的訂閱者可以使用這些配額為 Windows 虛擬桌面服務付費。  每月信用額度取決於訂閱級別。
- [Azure 開發人員測試即用即付訂閱](vs-azure-payg.md)。  您可以創建 Azure 訂閱並附加支付工具,以便以無縫方式為 Windows 虛擬桌面使用方式付費。 
- [Azure 企業協定開發測試產品 /服務](azure-ea-devtest.md)。  使用此產品/服務,具有企業協定的訂閱者可以以折扣價格使用 Azure 為 Windows 虛擬桌面付費。 

## <a name="requirements"></a>需求
Windows 虛擬桌面需要一個 Azure 活動目錄 (Azure AD),VM 將加入該目錄( Azure AD)  用戶必須是此 Azure AD 的成員。  實作 Azure AD 有兩個選項:
- Azure AD 目錄服務。  對於大多數使用者,這是更容易實現的選項。
- 運行域控制器促銷的虛擬機器。  此選項需要更多工作來設置,但為大多數使用者提供了更低的運營成本。
要檢視使用 Windows 虛擬桌面的先決條件的完整清單,請存取 Windows 虛擬桌面[概述頁](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)。 

## <a name="get-started"></a>開始使用 
當所有先決條件都到位時,您需要完成多個操作,以便實現到位。  請檢視以下教學以開始:
- [建立 Windows 虛擬桌面租戶](https://docs.microsoft.com/azure/virtual-desktop/tenant-setup-azure-active-directory)
- 使用 Azure 門戶[建立主機池](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace)
- 管理 Windows 虛擬桌面[的應用程式](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups)

## <a name="eligibility"></a>資格
| 訂用帳戶層級                                                 |     聲道                                            | 優點                                                          | 可續約？    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, 零售, | 可用|  是          |
| 含 GitHub Enterprise 的 Visual Studio Enterprise  | Vl | 可用|  是          |
| Visual Studio Professional (Standard) | VL, Azure, 零售                                       | 可用                                                             |  是             |
| 含 GitHub Enterprise 的 Visual Studio Professional | Vl                                       | 可用                                        |  是           |
| Visual Studio Test Professional (標準訂用帳戶)                         | VL, 零售                                              | 可用|  是          |
| MSDN 平台 (標準)                                          | VL, 零售                                              | 可用                                         |  是          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |無法使用  | N/A |
| Visual Studio Enterprise、Visual Studio Professional (每月雲端) | Azure | 無法使用 | N/A |

<sup>1</sup>  *包括: 不轉售 (NFR), FTE, 最有價值的專業人士 (MVP), 區域總監 (RD), 微軟合作夥伴網路 (MPN), 視覺工作室行業合作夥伴 (VSIP), 微軟認證培訓師, BizSpark, 想像*

> [!NOTE]
> Microsoft 不再於雲端訂用帳戶中提供 Visual Studio Professional 年度訂用帳戶和 Visual Studio Enterprise 年度訂用帳戶。 現有的客戶體驗，以及更新、增加、減少或取消其訂用帳戶的能力將不會改變。 我們鼓勵新客戶前往[https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/)探索購買 Visual Studio 的不同選項。

不確定您使用哪一個訂用帳戶？  連接到以查看[https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs)分配給您的電子郵件地址的所有訂閱。 若沒有看到您的所有訂用帳戶，可能有一或多個訂用帳戶是指派到不同的電子郵件地址。  您必須以該電子郵件地址登入才能查看對應的訂用帳戶。

## <a name="see-also"></a>另請參閱
- [Azure 文件](https://docs.microsoft.com/azure/)
- [Windows 虛擬桌面文件](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>後續步驟
-   如果您需要購買 Visual Studio 訂閱,請查看:
     - 通過 Microsoft 商店[進行零售採購的定價](https://visualstudio.microsoft.com/vs/pricing/)
     - [大量授權計劃](https://www.microsoft.com/licensing/default)
-   瞭解[Windows 虛擬桌面](https://docs.microsoft.com/azure/virtual-desktop/overview) 

---
title: 透過 Visual Studio 訂用帳戶中的終端機服務進行網際網路示範 |Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 03/21/2021
ms.topic: conceptual
description: 了解如何透過終端機服務使用產品金鑰來支援網際網路示範並啟用 RDS 存取
ms.openlocfilehash: c074dfe12ed7c1fea5ad60f7e0c8019e133a6d1b
ms.sourcegitcommit: d7d9fb79448b3534923cc95071d1f91eabde88e8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2021
ms.locfileid: "104776541"
---
# <a name="internet-demonstrations-via-terminal-services"></a>透過終端機服務存取網際網路示範
透過 Visual Studio 訂用帳戶，您可以授權使用者透過終端機服務 (Windows Server 2003 或 Windows Server 2008) 或遠端桌面服務 (Windows Server 2008 R2 及更新版本) 存取您程式的網際網路示範。 以這種方式同時存取示範的匿名使用者最多限 200 名。 示範絕對不可以使用生產資料。 Visual Studio 訂閱者享有向使用者示範其應用程式的權利。 使用終端機服務 (TS) 或遠端桌面服務 (RDS) 存取網際網路示範的目的，只在讓沒有 Visual Studio 訂用帳戶的使用者，可以在軟體經由 Visual Studio 訂用帳戶獲得授權之後，與示範應用程式互動。

這是開發/測試權利以外的權利，Visual Studio 訂閱者可以視需要建立所需數量的 RDS 或 TS 連線。

## <a name="enabling-rds-access"></a>啟用 RDS 存取
Visual Studio 訂閱者可輸入[訂閱者入口網站](https://my.visualstudio.com?wt.mc_id=o~msft~docs)上之 [[產品金鑰]](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) 索引標籤中所提供的產品金鑰，增加可以透過 RDS 存取 Windows Server 的使用者人數。 若要取得產品金鑰，請連線到 [產品金鑰] 頁面，並向下捲動到您所執行的 Windows Server 版本。 找到「Windows Server <版本> R2 遠端桌面服務 <使用者或裝置> 連線」，然後按一下 [領取金鑰] 按鈕。 例如，若是在 Windows Server 2012 R2 上使用 RDS，且您的部署使用使用者 CAL，請選擇 [Windows Server 2012 Remote Desktop Services 使用者連線 (50)]。
Windows Server 2008 R2 提供每種類型各五組金鑰，每組金鑰支援 20 個連線。 Windows Server 2012 R2 提供每種類型各四組金鑰，每組金鑰支援 50 個連線。

## <a name="to-enable-additional-connections-in-windows-server"></a>若要在 Windows Server 中允許更多的連線：
1. 開啟 [伺服器管理員]。
2. 開啟左側功能窗格中的 [伺服器] 清單。
3. 在您的授權伺服器上按一下滑鼠右鍵，然後選擇 [安裝授權]。
4. 請依照精靈中的步驟執行。  在選取合約類型時，選擇 [授權套件 (零售)]，然後輸入您從「我的」入口網站取得的產品金鑰。

符合下列條件的使用者，可以透過 RDS 連線來存取應用程式：
- 使用者必須匿名 (處於未經驗證的狀態)。
- 必須透過網際網路連線。
- 應用程式示範最多可有 200 個並行的使用者連線。
- 允許使用者連線的產品金鑰必須由 Visual Studio 訂閱者取得。

## <a name="support-resources"></a>支援資源
- 如需有關 Visual Studio 訂閱的銷售、訂用帳戶、帳戶和計費的協助，請聯絡 [Visual Studio 訂閱支援](https://aka.ms/vssubscriberhelp)。

## <a name="see-also"></a>另請參閱
- [Windows Server 文件](/windows-server/)
- [Visual Studio 檔](/visualstudio/)
- [Azure DevOps 文件](/azure/devops/) \(英文\)
- [Azure 檔](/azure/)
- [Microsoft 365 檔](/microsoft-365/)

## <a name="next-steps"></a>下一步
如果您需要部署 RDS 的指引，請參閱 **遠端桌面服務 (RDS) 2012 工作階段部署** (網址為 https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf) 的多部分部落格系列。 

如有任何問題，可前往 [Microsoft 遠端桌面服務論壇](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)。
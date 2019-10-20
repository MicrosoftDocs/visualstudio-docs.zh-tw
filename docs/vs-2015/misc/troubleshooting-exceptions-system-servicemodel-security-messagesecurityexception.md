---
title: 疑難排解例外狀況： MessageSecurityException |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: troubleshooting
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b8ce3f16c1439d62cfa1e2cff344b70e6724c42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655357"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>疑難排解例外狀況：System.ServiceModel.Security.MessageSecurityException
當 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] 判斷訊息未正確受到保護，或已遭篡改時，就會擲回 <xref:System.ServiceModel.Security.MessageSecurityException> 例外狀況。 這個錯誤通常是在下列所有條件都成立時發生：

- 在網站或 Web 應用程式專案中，您使用 WCF 服務參考透過遠端桌面連線或終端機服務 (Terminal Service) 這類的遠端連接，與 WCF 服務 (.svc) 通訊。

- 您沒有遠端站台的系統管理員權限。

- 遠端站台上 localhost 的要求是由 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 程式開發伺服器處理。

## <a name="associated-tips"></a>相關秘訣
 **解決使用 ASP.Net 程式開發伺服器時的 NTLM 驗證問題。**
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 程式開發伺服器通常會關閉 Windows NT 挑戰/回應 (NTLM) 安全性，以允許匿名存取。 根據預設，在執行終端機服務工作階段或使用遠端連接時，會啟用 NTLM 安全性。 啟用 NTLM 時，所有 localhost 要求都是針對啟動 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 程式開發伺服器的使用者或處理序的認證而驗證 (Validate) 的。 這樣會降低安全性威脅。 然而，WCF 也會執行自己的驗證 (Authentication)，且不允許系統管理員以外的帳戶使用 WCF 服務。

 如果遠端使用者可能會透過使用 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 程式開發伺服器執行網站，同時也會使用 Web 服務或 WCF 服務，您可以建立自訂服務繫結或是關閉 NTLM 安全性。

> [!IMPORTANT]
> 關閉 NTLM 安全性不是建議的方式，並且可能造成安全性威脅。

 如果您建立自訂服務繫結，則仍然受到 NTLM 驗證的保護。

 使用下列步驟，建立 WCF 服務的自訂服務繫結。

#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>若要為裝載於 ASP.NET 程式開發伺服器內的 WCF 服務建立自訂服務繫結

1. 開啟產生例外狀況的 WCF 服務的 Web.config 檔案。

2. 將下列資訊輸入到 Web.config 檔案中。

   ```
   <bindings>
     <customBinding>
       <binding name="Service1Binding">
         <transactionFlow />
         <textMessageEncoding />
         <httpTransport authenticationScheme="Ntlm" />
       </binding>
     </customBinding>
   </bindings>
   ```

3. 儲存並關閉 Web.config 檔案。

4. 在 WCF 或 Web 服務的程式碼中，將端點值變更成下列：

   ```
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />
   ```

    這樣可以確保服務會使用自訂繫結。

5. 在存取服務的 Web 應用程式中，加入服務的參考 (在 [ **加入服務參考** ] 對話方塊中，加入服務的參考，方法如同您在產生例外狀況的原始服務一樣)。

   當您使用 WCF 服務參考時，可以遵循下列步驟停用 NTLM 安全性。

> [!IMPORTANT]
> 關閉 NTLM 安全性不是建議的方式，並且可能造成安全性威脅。

#### <a name="to-turn-off-ntlm-security"></a>若要關閉 NTLM 安全性

1. 在 [ **方案總管**] 中，以滑鼠右鍵按一下網站名稱，然後再按一下 [ **屬性頁**]。

2. 選取 [ **起始選項**]，然後再清除 [ **NTLM 驗證** ] 核取方塊。

3. 按一下 [確定]。

## <a name="see-also"></a>請參閱
 <xref:System.ServiceModel.Security.MessageSecurityException>[使用例外狀況助理](https://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)
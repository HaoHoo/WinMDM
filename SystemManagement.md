# 基于Windows 10 MDM的系统管理

## 1. 使用MDM框架的CSP添加本地管理员

```XML
```
## 2. 使用MDM框架远程配置系统锁屏和桌面墙纸

```XML
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Replace>
      <CmdID>1</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/Personalization/LockScreenImageUrl
          </LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">chr</Format>
          <Type>text/plain</Type>
        </Meta>
        <Data>https://github.com/HaoHoo/WinMDM/raw/master/resource/locking.jpg</Data>
      </Item>
    </Replace>
    <Replace>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>
            ./Vendor/MSFT/Personalization/DesktopImageUrl
          </LocURI>
        </Target>
        <Meta>
          <Format xmlns="syncml:metinf">chr</Format>
          <Type>text/plain</Type>
        </Meta>
        <Data>https://github.com/HaoHoo/WinMDM/raw/master/resource/desktop.jpg</Data>
      </Item>
    </Replace>
    <Final/> 
  </SyncBody>
</SyncML>
```

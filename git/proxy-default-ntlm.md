# Proxy with default NTLM credentials

In order to use default NTLM credentials, provide an empty username and password:

```
git config --global http.proxy https://:@proxy:port
```

To remove proxy settings use:

```
git config --global --unset http.proxy
```


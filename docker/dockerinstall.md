### Simple bash script to install docker. This is just an example, needs to be adjusted for other applications

```bash
#!/bin/bash
# docker install + proxy configuration

apt-get update
apt-get install -y apt-transport-https ca-certificates

# Add sources depending on debian version
version=$(head -c 1 /etc/debian_version)
sourcelist="/etc/apt/sources.list"
if [ "$versioin" = "9" ]
 then if ! grep -q "deb https://apt.dockerproject.org/repo debian-stretch main" "$sourcelist";
  then echo "deb https://apt.dockerproject.org/repo debian-stretch main" >> "$sourcelist"
 fi
elif [ "$version" = "8" ]
 then if ! grep -q "deb https://apt.dockerproject.org/repo debian-jessie main" "$sourcelist";
  then echo "deb https://apt.dockerproject.org/repo debian-jessie main" >> "$sourcelist"
 fi
elif [ "$versioin" = "7" ]
 then if ! grep -q "deb https://apt.dockerproject.org/repo debian-wheezy main" "$sourcelist";
  then echo "deb https://apt.dockerproject.org/repo debian-wheezy main" >> "$sourcelist"
 fi
fi

apt-get update
echo "docker-engine package will not be authenticated!"
apt-get install -y --force-yes docker-engine

# setup registry certificate

# setup registry certificate

mkdir /etc/docker/certs.d
certdir="/etc/docker/certs.d/DE9899SRZ.domain.local:28080"
mkdir $certdir

echo -----BEGIN CERTIFICATE----- > $certdir/ca.crt
echo MIIGTDCCBDSgAwIBAgIJAM2rp4srYk0+MA0GCSqGSIb3DQEBCwUAMIGzMQswCQYD >> $certdir/ca.crt
echo VQQGEwJERTETMBEGA1UECAwKU29tZS1TdGF0ZTERMA8GA1UEBwwITMODwrxuZW4x >> $certdir/ca.crt
echo KzApBgNVBAoMIlJFTU9ORElTIElUIFNlcnZpY2VzIEdtYkggJiBDby4gS0cxJDAi >> $certdir/ca.crt
echo BgNVBAMMG0RFOTg5OVNSWi5yZW1vbmRpcy1kZS5sb2NhbDEpMCcGCSqGSIb3DQEJ >> $certdir/ca.crt
echo ARYaaGVucnkuZWlkZWNrZXJAcmVtb25kaXMuZGUwHhcNMTYwNzEzMDgwNDM4WhcN >> $certdir/ca.crt
echo MTcwNzEzMDgwNDM4WjCBszELMAkGA1UEBhMCREUxEzARBgNVBAgMClNvbWUtU3Rh >> $certdir/ca.crt
echo dGUxETAPBgNVBAcMCEzDg8K8bmVuMSswKQYDVQQKDCJSRU1PTkRJUyBJVCBTZXJ2 >> $certdir/ca.crt
echo aWNlcyBHbWJIICYgQ28uIEtHMSQwIgYDVQQDDBtERTk4OTlTUloucmVtb25kaXMt >> $certdir/ca.crt
echo ZGUubG9jYWwxKTAnBgkqhkiG9w0BCQEWGmhlbnJ5LmVpZGVja2VyQHJlbW9uZGlz >> $certdir/ca.crt
echo LmRlMIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAljyTJ2nXu7REC0O/ >> $certdir/ca.crt
echo U+Nl8EX/Lo2FSjEUC465TGxP02EUS8GFgehEeFmTS54jTmh0huYBbQ5SmAhEOaeh >> $certdir/ca.crt
echo Wlb4gcBWZDD+q2JuK+0rprGOvoza9VE7FL4DU4LGJSYYakAR/XUypmuFYOEZ8pxx >> $certdir/ca.crt
echo lBlU3xVQMHAu74jPShLopRlk172WkbrxjBL47ckTvSPSuGOIH8c34NyEllETPKwJ >> $certdir/ca.crt
echo aq61gDU/OwltuWYnylF4TxYrk3TLuDT/S4wS6Ieu0pyFVJLwoEa94XFB0x4rtvZX >> $certdir/ca.crt
echo BDv/M4O6unr/JTBZPL7DPbYGMYjYa6BV7gojPc0RVDzP73GAw8b8GNigRFFVbr7g >> $certdir/ca.crt
echo +NRxC6OomLgZOc3TomoEujfXfei9TTxg9+WEHxhepPiIsuA0GJOl6tvrVks4ICju >> $certdir/ca.crt
echo WX4LRXsK+fWBA9kUsuGbkV/kBrCW4o1z1rfjb6dWJTyRm4Fvy3dPrclbsoEIwqKN >> $certdir/ca.crt
echo pGSpNT7JsKw6a+UwmpzuXErY339j18CHcgiA+TulLnvh6LXHKCLLjjlfFOMzVV2N >> $certdir/ca.crt
echo CpFlpVPuZKGbE9XVFDVXVcV7rwJIbhzrbP42MxVY9NzyhIEHIqupRJrffvXyp1Fh >> $certdir/ca.crt
echo 8jnvSJxeMV+e0Hln2tZf85eqMUCLB/mkLuj54AtoxRp9+sqf2c8SKJZcwOsriK80 >> $certdir/ca.crt
echo YVF9xHMy86T2c7xCPDB+ON4/HUMCAwEAAaNhMF8wHQYDVR0OBBYEFGSgnxPJElTW >> $certdir/ca.crt
echo PHaoQx9xCOknWIR5MB8GA1UdIwQYMBaAFGSgnxPJElTWPHaoQx9xCOknWIR5MAwG >> $certdir/ca.crt
echo A1UdEwQFMAMBAf8wDwYDVR0RBAgwBocECgIrGjANBgkqhkiG9w0BAQsFAAOCAgEA >> $certdir/ca.crt
echo OeHrVnB17rR4eg0ONHGSIPxHcfrdkYIVjD0agtFsTRorFRo7/9Fzxm/wkFXqlhs8 >> $certdir/ca.crt
echo PSG/ZdCTB9PT+2x64k+F7rFdd9A7tv2wOZX41ucQ/xG4ePcz9yHDCzEep5qUsqLf >> $certdir/ca.crt
echo PyHRfHLpk2iXJV9+jVgvUFA1MgOuPKQtOyECtImPYl0+/qyGrtQATWBJUONHR06s >> $certdir/ca.crt
echo A0aGinBI2Z4O97zFSFIow9a09RRY4u3pGgqbTjpVcQP9gZAR8oqu6s3I7/RjFyhl >> $certdir/ca.crt
echo knBdjoJ+tiRP6eUHuKhwSsahNIJy1KsjI6Kb5NwI7dnJXMmitkUq2gC/aERfofZ8 >> $certdir/ca.crt
echo Dh57QMgcuZQLA/yd+nYjbC/SydlfOJxnmr0vp5QDpx/MwaLNCdFs0xG9RTDi/91C >> $certdir/ca.crt
echo keBT2W7fLD1kXF1LUM7HQITR3U64S2YEXP9Hj9XLSa0W35uZACUIX536ELGOIfpC >> $certdir/ca.crt
echo W+6bggpV9DebrBT9Awn3OK9Z4GU0UydqBFy4mE+utkzs7WrkyZDtvq12IqNG+O3x >> $certdir/ca.crt
echo cuApHTLinUMU+8bHpa0OfkfdWVUJfTjGngA5vZ3iBxfbCmGlxTbscios98XavbRJ >> $certdir/ca.crt
echo pIlDAg4mHA17gkozqJEUwqrCXL6d8saarL0f/f59FPtTB7gG4oa1a6xUdS8X5MUR >> $certdir/ca.crt
echo RiwyaTOG8o7fjYO+EbxXJN6iv9uUPOTpbgT9pVECmFA= >> $certdir/ca.crt
echo -----END CERTIFICATE----- >> $certdir/ca.crt

service docker stop && service docker start
```

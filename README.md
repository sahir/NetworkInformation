# NetworkInformation
check if a TCP port is available


TcpClient checking open TCP ports. There are lots of good objects available in the System.Net.NetworkInformation namespace.

Use the IPGlobalProperties object to get to an array of  TcpConnectionInformation objects, which you can then interrogate about endpoint IP and port.

                ```
                int port = 8008;
                IPAddress localAddr = IPAddress.Parse("127.0.0.1");


                bool isAvailable = true;

                IPGlobalProperties ipGlobalProperties = IPGlobalProperties.GetIPGlobalProperties();
                TcpConnectionInformation[] tcpConnInfoArray = ipGlobalProperties.GetActiveTcpConnections();

                IPEndPoint[] endPoints = ipGlobalProperties.GetActiveTcpListeners();

                foreach (IPEndPoint e in endPoints)
                {
                    Console.WriteLine(e.Port.ToString());

                    if (e.Port == port)
                    {
                        isAvailable = false;
                        break;
                    }
                   
                }

                Console.Write("\n"+isAvailable);
                ```

# Relatório Roteamento Estático

Para realizar o experimento de roteamento estático, seguindo o cenário descrito com as máquinas A, B e o computador Linux (R), os seguintes passos devem ser seguidos:

Materiais necessários:

1. 3 computadores (A, B e R) com pelo menos duas interfaces de rede cada.
2. Adaptadores USB/Ethernet, se as máquinas não tiverem duas interfaces de rede integradas.
3. Cabos Ethernet (patch cords) e um switch de 8 portas, se desejar conectar mais máquinas às redes locais.

Passos:

1. Configure as interfaces de rede dos computadores A, B e R:
    - No computador A:
        - Configure a interface com o IP 192.168.1.2/24.
        - Defina a máscara de sub-rede como 255.255.255.0.
    - No computador B:
        - Configure a interface com o IP 172.25.0.2/16.
        - Defina a máscara de sub-rede como 255.255.0.0.
    - No computador Linux (R):
        - Configure a primeira interface com o IP 192.168.1.1/24 e conecte-a à mesma rede que o computador A.
        - Configure a segunda interface com o IP 172.25.0.1/16 e conecte-a à mesma rede que o computador B.
2. Certifique-se de que todas as interfaces de rede estejam ativadas em cada computador.
3. No computador Linux (R), habilite o roteamento IP para permitir que ele encaminhe o tráfego entre as duas redes. Para fazer isso, você pode usar o seguinte comando no terminal:
    
    ```
    sudo sysctl -w net.ipv4.ip_forward=1
    
    ```
    
    Isso permitirá que o Linux (R) encaminhe pacotes entre as duas redes.
    
4. Agora, você deve ser capaz de realizar o ping de A para B e vice-versa, pois o computador Linux (R) funcionará como um roteador entre as duas redes locais.
5. Para testar a conectividade, abra um terminal no computador A e execute o seguinte comando:
    
    ```
    ping 172.25.0.2
    
    ```
    
    E no computador B, execute:
    
    ```
    ping 192.168.1.2
    
    ```
    
    Isso deve permitir que você verifique a conectividade entre as duas máquinas em redes diferentes através do computador Linux (R).
    

Esse é um cenário de roteamento estático simples. Se você quiser explorar protocolos de roteamento dinâmico como RIP ou OSPF, precisará configurar esses protocolos nos roteadores. Além disso, se desejar adicionar mais máquinas às redes locais, você pode usar um switch para conectá-las. Certifique-se de configurar as interfaces de rede corretamente em cada máquina nova.

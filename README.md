# Python-Server-
Configure Python sever (Able to run python Script as web App ) 
Stept to configure 

1- apt-get -y install python 
2- a2enmod cgi 
3- systemctl restart apache2
4- #test Script 

    cat> /usr/lib/cgi-bin/test_script <<'EOF'
    #!/usr/bin/env python 
    print "Content-type:text/html\n\n"
    print "Hello CGI\n"
    EOF
5-chmod 705 /usr/lib/cgi-bin/test_script 
6-curl http://localhost/cgi-bin/test_script 
7- nano /etc/apache2/conf-available/cgi-enabled.conf

      #create new 
      # processes .cgi and .py as CGI scripts 
      <Directory "var/www/html/cgi-enabled">
        options +ExecCGI
        AddHandler cgi-script .cgi .py   
      </Directory> 

8-mkdir /var/www/html/cgi-enabled
9-a2enconf cgi-enabled
10-systemctl restart apache2 

11- nano /var/www/cgi-enabled/index.py 

12- chmod 705 /var/www/cgi-enabled/index.p

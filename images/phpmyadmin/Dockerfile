FROM phpmyadmin/phpmyadmin:4.9

# increace maximum execution time for large files
RUN echo '$cfg['ExecTimeLimit'] = 6000;' >> /etc/phpmyadmin/config.inc.php
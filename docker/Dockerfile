FROM python:2.7

USER root
RUN apt update && apt -y upgrade && apt install -y unzip

RUN pip install MySQL-python

RUN git clone https://github.com/urmilparikh/Quillpad-Server.git /qs

WORKDIR /qs
RUN cd /qs/Python\ Cart/python/ && python setup.py build_ext --inplace && cp QuillCCart.so ../../
RUN cd /qs && for file in *.zip; do unzip $file; rm $file; done && for file in *.tar.*; do tar xf $file; rm $file; done
RUN cd /qs && mv CherryPy-3.2.2/cherrypy/ ./ && mv Pyrex-0.9.9/Pyrex/ ./ && rm -rf CherryPy-3.2.2 Pyrex-0.9.9
RUN mkdir -p /qs/logs

EXPOSE 8090

CMD python startquill_cherry.py

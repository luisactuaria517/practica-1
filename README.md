# practica-1
r truco descargar archivos directos

temporal <- tempfile()
download.file("http://www.beta.inegi.org.mx/contenidos/proyectos/enchogares/regulares/enoe/microdatos/enoe_15ymas/2016/2016trim1_dbf.zip", temporal)
# el lick es la liga de descarga del archivo en zip
files=unzip(temporal, list = TRUE)$Name
unzip(temporal, files = files[grepl("dbf",files)])
install.packages("foreign")
require(foreign)
sdemt116<-data.frame(read.dbf("sdemt116.dbf"))
# "sdemt116" se uso xk es el nombre del archivo de la base de datos
View(sdemt116)

nombres <- c("sergio", "carlos", "paula")
nombres
edad <- c(23,43,51)
edad
base1<- data.frame(nombres,edad)
base1
table(sdemt116$SEX)
table(sdemt116$ENT)
install.packages("questionr")#libreria
require(questionr)#llamar la libreria a sesion de r (permnente)
wtd.table (sdemt116$SEX, weights = sdemt116$FAC)

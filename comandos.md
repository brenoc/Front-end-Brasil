## Lê CSV
dados <- read.csv(file="respostas.csv",head=TRUE,sep=",")

## Apenas os que moram no Brasil

dados <- subset(dados, dados["BRA"] == "S")

## Condicionais

#condFrontEnd = (dados["PER"] == "B" | dados["FOC"] == "S")
#condBackEnd = (dados["PER"] == "A" & dados["FOC"] == "N")

condFrontEnd = (dados["PER"] == "B" | (dados["FOC"] == "S" & dados["PER"] != "A"))
condBackEnd = (dados["PER"] == "A")

condUsaFrameworksJS = (dados["FRW.ANG"] == 1 | dados["FRW.BBO"] == 1 | dados["FRW.EMB"] == 1 | dados["FRW.KNO"] == 1 | dados["FRW.OTH"] == 1)
condUsaApenasJquery = (is.na(dados["FRW.ANG"]) & is.na(dados["FRW.BBO"]) & is.na(dados["FRW.EMB"]) & is.na(dados["FRW.KNO"]) & is.na(dados["FRW.OTH"]) & dados["FRW.JQU"] == 1)

condInexperientes = (dados["EXP"] == "A")
condPoucoExperientes = (dados["EXP"] == "B")
condExperientes = (dados["EXP"] == "C")
condExperts = (dados["EXP"] == "D")

condUsaModule = (dados["MOD"] == "S")
condNaoUsaModule = (dados["MOD"] == "N")
condNaoSabeModule = (dados["MOD"] == "U")

condUsaPackageManager = (dados["PKG"] == "S")
condNaoUsaPackageManager = (dados["PKG"] == "N")

condUsaAutomat = (dados["AUT"] == "S")
condNaoUsaAutomat = (dados["AUT"] == "N")

condFazTestes = (dados["TST"] == "S")
condNaoFazTestes = (dados["TST"] == "N")

condUsaFerrTestes = (dados["TST.FER"] == "S")
condNaoUsaFerrTestes = (dados["TST.FER"] == "N")

condUsaContrVer = (dados["VER"] == "S")
condNaoUsaContrVer = (dados["VER"] == "N")

condUsaPreProCSS = (dados["PCS"] == "S")
condNaoUsaPreProCSS = (dados["PCS"] == "N")

condUsaFrameworkCSS = (dados["CSS"] == "S")
condNaoUsaFrameworkCSS = (dados["CSS"] == "N")

condUsaTemplateEng = (dados["TMP"] == "S")
condNaoUsaTemplateEng = (dados["TMP"] == "N")

condUsaOutraLing = (dados["LNG"] == "S")
condNaoUsaOutraLing = (dados["LNG"] == "N")

## Subsets

## Perfis
ssBackEnd <- subset(dados, condBackEnd)
ssFrontEnd <- subset(dados, condFrontEnd)

## Frameworks JS
ssBackEndFrameworksJS <- subset(dados, condUsaFrameworksJS & condBackEnd)
ssBackEndSoJquery <- subset(dados, condUsaApenasJquery & condBackEnd)
ssFrontEndFrameworksJS <- subset(dados, condUsaFrameworksJS & condFrontEnd)
ssFrontEndSoJquery <- subset(dados, condUsaApenasJquery & condFrontEnd)

## Experiência dos desenvolvedores Front-end
ssFrontEndInexperientes <- subset(dados, condInexperientes & condFrontEnd)
ssFrontEndPoucoExperientes <- subset(dados, condPoucoExperientes & condFrontEnd)
ssFrontEndExperientes <- subset(dados, condExperientes & condFrontEnd)
ssFrontEndExperts <- subset(dados, condExperts & condFrontEnd)

## Experiência dos desenvolvedores Back-end
ssBackEndInexperientes <- subset(dados, condInexperientes & condBackEnd)
ssBackEndPoucoExperientes <- subset(dados, condPoucoExperientes & condBackEnd)
ssBackEndExperientes <- subset(dados, condExperientes & condBackEnd)
ssBackEndExperts <- subset(dados, condExperts & condBackEnd)



## Novas Ferramentas e Práticas

### Back-end
ssBackEndUsaModulo <- subset(dados, condUsaModule & condBackEnd)
ssBackEndUsaPackageManager <- subset(dados, condUsaPackageManager & condBackEnd)
ssBackEndUsaAutomat <- subset(dados, condUsaAutomat & condBackEnd)
ssBackEndFazTestes <- subset(dados, condFazTestes & condBackEnd)
ssBackEndUsaContrVer <- subset(dados, condUsaContrVer & condBackEnd)
ssBackEndUsaPreProCSS <- subset(dados, condUsaPreProCSS & condBackEnd)
ssBackEndUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condBackEnd)
ssBackEndUsaTemplateEng <- subset(dados, condUsaTemplateEng & condBackEnd)
ssBackEndUsaOutraLing <- subset(dados, condUsaOutraLing & condBackEnd)

#### Divido por Experiência

##### Inexperientes
ssBackEndInexperienteUsaModulo <- subset(dados, condUsaModule & condInexperientes & condBackEnd)
ssBackEndInexperienteUsaPackageManager <- subset(dados, condUsaPackageManager & condInexperientes & condBackEnd)
ssBackEndInexperienteUsaAutomat <- subset(dados, condUsaAutomat & condInexperientes & condBackEnd)
ssBackEndInexperienteFazTestes <- subset(dados, condFazTestes & condInexperientes & condBackEnd)
ssBackEndInexperienteUsaContrVer <- subset(dados, condUsaContrVer & condInexperientes & condBackEnd)
ssBackEndInexperienteUsaPreProCSS <- subset(dados, condUsaPreProCSS & condInexperientes & condBackEnd)
ssBackEndInexperienteUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condInexperientes & condBackEnd)
ssBackEndInexperienteUsaTemplateEng <- subset(dados, condUsaTemplateEng & condInexperientes & condBackEnd)
ssBackEndInexperienteUsaOutraLing <- subset(dados, condUsaOutraLing & condInexperientes & condBackEnd)

##### Pouco Experientes
ssBackEndPoucoExperienteUsaModulo <- subset(dados, condUsaModule & condPoucoExperientes & condBackEnd)
ssBackEndPoucoExperienteUsaPackageManager <- subset(dados, condUsaPackageManager & condPoucoExperientes & condBackEnd)
ssBackEndPoucoExperienteUsaAutomat <- subset(dados, condUsaAutomat & condPoucoExperientes & condBackEnd)
ssBackEndPoucoExperienteFazTestes <- subset(dados, condFazTestes & condPoucoExperientes & condBackEnd)
ssBackEndPoucoExperienteUsaContrVer <- subset(dados, condUsaContrVer & condPoucoExperientes & condBackEnd)
ssBackEndPoucoExperienteUsaPreProCSS <- subset(dados, condUsaPreProCSS & condPoucoExperientes & condBackEnd)
ssBackEndPoucoExperienteUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condPoucoExperientes & condBackEnd)
ssBackEndPoucoExperienteUsaTemplateEng <- subset(dados, condUsaTemplateEng & condPoucoExperientes & condBackEnd)
ssBackEndPoucoExperienteUsaOutraLing <- subset(dados, condUsaOutraLing & condPoucoExperientes & condBackEnd)

##### Experientes
ssBackEndExperienteUsaModulo <- subset(dados, condUsaModule & condExperientes & condBackEnd)
ssBackEndExperienteUsaPackageManager <- subset(dados, condUsaPackageManager & condExperientes & condBackEnd)
ssBackEndExperienteUsaAutomat <- subset(dados, condUsaAutomat & condExperientes & condBackEnd)
ssBackEndExperienteFazTestes <- subset(dados, condFazTestes & condExperientes & condBackEnd)
ssBackEndExperienteUsaContrVer <- subset(dados, condUsaContrVer & condExperientes & condBackEnd)
ssBackEndExperienteUsaPreProCSS <- subset(dados, condUsaPreProCSS & condExperientes & condBackEnd)
ssBackEndExperienteUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condExperientes & condBackEnd)
ssBackEndExperienteUsaTemplateEng <- subset(dados, condUsaTemplateEng & condExperientes & condBackEnd)
ssBackEndExperienteUsaOutraLing <- subset(dados, condUsaOutraLing & condExperientes & condBackEnd)

##### Experts
ssBackEndExpertUsaModulo <- subset(dados, condUsaModule & condExperts &condBackEnd)
ssBackEndExpertUsaPackageManager <- subset(dados, condUsaPackageManager & condExperts &condBackEnd)
ssBackEndExpertUsaAutomat <- subset(dados, condUsaAutomat & condExperts &condBackEnd)
ssBackEndExpertFazTestes <- subset(dados, condFazTestes & condExperts &condBackEnd)
ssBackEndExpertUsaContrVer <- subset(dados, condUsaContrVer & condExperts &condBackEnd)
ssBackEndExpertUsaPreProCSS <- subset(dados, condUsaPreProCSS & condExperts &condBackEnd)
ssBackEndExpertUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condExperts &condBackEnd)
ssBackEndExpertUsaTemplateEng <- subset(dados, condUsaTemplateEng & condExperts &condBackEnd)
ssBackEndExpertUsaOutraLing <- subset(dados, condUsaOutraLing & condExperts &condBackEnd)


### Front-end
ssFrontEndUsaModulo <- subset(dados, condUsaModule & condFrontEnd)
ssFrontEndUsaPackageManager <- subset(dados, condUsaPackageManager & condFrontEnd)
ssFrontEndUsaAutomat <- subset(dados, condUsaAutomat & condFrontEnd)
ssFrontEndFazTestes <- subset(dados, condFazTestes & condFrontEnd)
ssFrontEndUsaContrVer <- subset(dados, condUsaContrVer & condFrontEnd)
ssFrontEndUsaPreProCSS <- subset(dados, condUsaPreProCSS & condFrontEnd)
ssFrontEndUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condFrontEnd)
ssFrontEndUsaTemplateEng <- subset(dados, condUsaTemplateEng & condFrontEnd)
ssFrontEndUsaOutraLing <- subset(dados, condUsaOutraLing & condFrontEnd)

#### Divido por Experiência

##### Inexperientes
ssFrontEndInexperienteUsaModulo <- subset(dados, condUsaModule & condInexperientes & condFrontEnd)
ssFrontEndInexperienteUsaPackageManager <- subset(dados, condUsaPackageManager & condInexperientes & condFrontEnd)
ssFrontEndInexperienteUsaAutomat <- subset(dados, condUsaAutomat & condInexperientes & condFrontEnd)
ssFrontEndInexperienteFazTestes <- subset(dados, condFazTestes & condInexperientes & condFrontEnd)
ssFrontEndInexperienteUsaContrVer <- subset(dados, condUsaContrVer & condInexperientes & condFrontEnd)
ssFrontEndInexperienteUsaPreProCSS <- subset(dados, condUsaPreProCSS & condInexperientes & condFrontEnd)
ssFrontEndInexperienteUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condInexperientes & condFrontEnd)
ssFrontEndInexperienteUsaTemplateEng <- subset(dados, condUsaTemplateEng & condInexperientes & condFrontEnd)
ssFrontEndInexperienteUsaOutraLing <- subset(dados, condUsaOutraLing & condInexperientes & condFrontEnd)

##### Pouco Experientes
ssFrontEndPoucoExperienteUsaModulo <- subset(dados, condUsaModule & condPoucoExperientes & condFrontEnd)
ssFrontEndPoucoExperienteUsaPackageManager <- subset(dados, condUsaPackageManager & condPoucoExperientes & condFrontEnd)
ssFrontEndPoucoExperienteUsaAutomat <- subset(dados, condUsaAutomat & condPoucoExperientes & condFrontEnd)
ssFrontEndPoucoExperienteFazTestes <- subset(dados, condFazTestes & condPoucoExperientes & condFrontEnd)
ssFrontEndPoucoExperienteUsaContrVer <- subset(dados, condUsaContrVer & condPoucoExperientes & condFrontEnd)
ssFrontEndPoucoExperienteUsaPreProCSS <- subset(dados, condUsaPreProCSS & condPoucoExperientes & condFrontEnd)
ssFrontEndPoucoExperienteUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condPoucoExperientes & condFrontEnd)
ssFrontEndPoucoExperienteUsaTemplateEng <- subset(dados, condUsaTemplateEng & condPoucoExperientes & condFrontEnd)
ssFrontEndPoucoExperienteUsaOutraLing <- subset(dados, condUsaOutraLing & condPoucoExperientes & condFrontEnd)

##### Experientes
ssFrontEndExperienteUsaModulo <- subset(dados, condUsaModule & condExperientes & condFrontEnd)
ssFrontEndExperienteUsaPackageManager <- subset(dados, condUsaPackageManager & condExperientes & condFrontEnd)
ssFrontEndExperienteUsaAutomat <- subset(dados, condUsaAutomat & condExperientes & condFrontEnd)
ssFrontEndExperienteFazTestes <- subset(dados, condFazTestes & condExperientes & condFrontEnd)
ssFrontEndExperienteUsaContrVer <- subset(dados, condUsaContrVer & condExperientes & condFrontEnd)
ssFrontEndExperienteUsaPreProCSS <- subset(dados, condUsaPreProCSS & condExperientes & condFrontEnd)
ssFrontEndExperienteUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condExperientes & condFrontEnd)
ssFrontEndExperienteUsaTemplateEng <- subset(dados, condUsaTemplateEng & condExperientes & condFrontEnd)
ssFrontEndExperienteUsaOutraLing <- subset(dados, condUsaOutraLing & condExperientes & condFrontEnd)

##### Experts
ssFrontEndExpertUsaModulo <- subset(dados, condUsaModule & condExperts & condFrontEnd)
ssFrontEndExpertUsaPackageManager <- subset(dados, condUsaPackageManager & condExperts & condFrontEnd)
ssFrontEndExpertUsaAutomat <- subset(dados, condUsaAutomat & condExperts & condFrontEnd)
ssFrontEndExpertFazTestes <- subset(dados, condFazTestes & condExperts & condFrontEnd)
ssFrontEndExpertUsaContrVer <- subset(dados, condUsaContrVer & condExperts & condFrontEnd)
ssFrontEndExpertUsaPreProCSS <- subset(dados, condUsaPreProCSS & condExperts & condFrontEnd)
ssFrontEndExpertUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condExperts & condFrontEnd)
ssFrontEndExpertUsaTemplateEng <- subset(dados, condUsaTemplateEng & condExperts & condFrontEnd)
ssFrontEndExpertUsaOutraLing <- subset(dados, condUsaOutraLing & condExperts & condFrontEnd)

# Variaveis

nBackEnd = nrow(ssBackEnd)
nBackEnd100 = nBackEnd / 100
nBackEndInexperientes = nrow(ssBackEndInexperientes)
nBackEndPoucoExperientes = nrow(ssBackEndPoucoExperientes)
nBackEndExperientes = nrow(ssBackEndExperientes)
nBackEndExperts = nrow(ssBackEndExperts)
nBackEndInexperientes100 = nrow(ssBackEndInexperientes) / 100
nBackEndPoucoExperientes100 = nrow(ssBackEndPoucoExperientes) / 100
nBackEndExperientes100 = nrow(ssBackEndExperientes) / 100
nBackEndExperts100 = nrow(ssBackEndExperts) / 100

nFrontEnd = nrow(ssFrontEnd)
nFrontEnd100 = nFrontEnd / 100
nFrontEndInexperientes = nrow(ssFrontEndInexperientes)
nFrontEndPoucoExperientes = nrow(ssFrontEndPoucoExperientes)
nFrontEndExperientes = nrow(ssFrontEndExperientes)
nFrontEndExperts = nrow(ssFrontEndExperts)
nFrontEndInexperientes100 = nrow(ssFrontEndInexperientes) / 100
nFrontEndPoucoExperientes100 = nrow(ssFrontEndPoucoExperientes) / 100
nFrontEndExperientes100 = nrow(ssFrontEndExperientes) / 100
nFrontEndExperts100 = nrow(ssFrontEndExperts) / 100

nDados = nrow(dados)
nDados100 = nDados / 100

cFerramPraticas =c("Module\nPattern", "Package\nManager", "Ferramenta\n de Automatizacao\nde Tarefas", "Testes", "Controle\nVersão", "Pré-processador\nCSS", "Framework CSS", "Template Engine", "Outra\nLinguagem para JS")

# Gráficos

### Comparação da Experiência em Front-end
aBackEndExp = c(nBackEndInexperientes / nBackEnd100, nBackEndPoucoExperientes / nBackEnd100, nBackEndExperientes / nBackEnd100, nBackEndExperts / nBackEnd100)
aFrontEndExp = c(nFrontEndInexperientes / nFrontEnd100, nFrontEndPoucoExperientes / nFrontEnd100, nFrontEndExperientes / nFrontEnd100, nFrontEndExperts / nFrontEnd100)
barplot(matrix(c(aBackEndExp, aFrontEndExp), 2, byrow=T), ylim=c(0,100), xlim=c(0,10), ylab="%", beside=T, space=c(0,0.2), density=5, angle=0, col=c("blue", "red"), names.arg=c("Inexperientes", "Pouco Experientes", "Experientes", "Experts"), main="Comparaçao\nda Experiência em Front-end", legend.text=c("Back-end", "Front-end"))


## Uso de Novas Ferramentas e Práticas

### Desenvolvedores Back-end
aBackEndPraticas = c(nrow(ssBackEndUsaModulo)/nBackEnd100, nrow(ssBackEndUsaPackageManager)/nBackEnd100, nrow(ssBackEndUsaAutomat)/nBackEnd100, nrow(ssBackEndFazTestes)/nBackEnd100, nrow(ssBackEndUsaContrVer)/nBackEnd100, nrow(ssBackEndUsaPreProCSS)/nBackEnd100, nrow(ssBackEndUsaFrameworkCSS)/nBackEnd100, nrow(ssBackEndUsaTemplateEng)/nBackEnd100, nrow(ssBackEndUsaOutraLing)/nBackEnd100)
barplot(aBackEndPraticas, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Back-end")

#### Dividido por Experiência

#### Inexperientes
aBackEndPraticasInexperientes = c(nrow(ssBackEndInexperienteUsaModulo)/nBackEndInexperientes100, nrow(ssBackEndInexperienteUsaPackageManager)/nBackEndInexperientes100, nrow(ssBackEndInexperienteUsaAutomat)/nBackEndInexperientes100, nrow(ssBackEndInexperienteFazTestes)/nBackEndInexperientes100, nrow(ssBackEndInexperienteUsaContrVer)/nBackEndInexperientes100, nrow(ssBackEndInexperienteUsaPreProCSS)/nBackEndInexperientes100, nrow(ssBackEndInexperienteUsaFrameworkCSS)/nBackEndInexperientes100, nrow(ssBackEndInexperienteUsaTemplateEng)/nBackEndInexperientes100, nrow(ssBackEndInexperienteUsaOutraLing)/nBackEndInexperientes100)	
barplot(aBackEndPraticasInexperientes, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Back-end Inexperientes")

#### Pouco Experientes
aBackEndPraticasPoucoExperientes = c(nrow(ssBackEndPoucoExperienteUsaModulo)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteUsaPackageManager)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteUsaAutomat)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteFazTestes)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteUsaContrVer)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteUsaPreProCSS)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteUsaFrameworkCSS)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteUsaTemplateEng)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteUsaOutraLing)/nBackEndPoucoExperientes100)
barplot(aBackEndPraticasPoucoExperientes, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Back-end Pouco Experientes")

#### Experientes
aBackEndPraticasExperientes = c(nrow(ssBackEndExperienteUsaModulo)/nBackEndExperientes100, nrow(ssBackEndExperienteUsaPackageManager)/nBackEndExperientes100, nrow(ssBackEndExperienteUsaAutomat)/nBackEndExperientes100, nrow(ssBackEndExperienteFazTestes)/nBackEndExperientes100, nrow(ssBackEndExperienteUsaContrVer)/nBackEndExperientes100, nrow(ssBackEndExperienteUsaPreProCSS)/nBackEndExperientes100, nrow(ssBackEndExperienteUsaFrameworkCSS)/nBackEndExperientes100, nrow(ssBackEndExperienteUsaTemplateEng)/nBackEndExperientes100, nrow(ssBackEndExperienteUsaOutraLing)/nBackEndExperientes100)	
barplot(aBackEndPraticasExperientes, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Back-end Experientes")

#### Experts
aBackEndPraticasExperts = c(nrow(ssBackEndExpertUsaModulo)/nBackEndExperts100, nrow(ssBackEndExpertUsaPackageManager)/nBackEndExperts100, nrow(ssBackEndExpertUsaAutomat)/nBackEndExperts100, nrow(ssBackEndExpertFazTestes)/nBackEndExperts100, nrow(ssBackEndExpertUsaContrVer)/nBackEndExperts100, nrow(ssBackEndExpertUsaPreProCSS)/nBackEndExperts100, nrow(ssBackEndExpertUsaFrameworkCSS)/nBackEndExperts100, nrow(ssBackEndExpertUsaTemplateEng)/nBackEndExperts100, nrow(ssBackEndExpertUsaOutraLing)/nBackEndExperts100)	
barplot(aBackEndPraticasExperts, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Back-end Experts")

#### Comparando
barplot(matrix(c(aBackEndPraticasInexperientes, aBackEndPraticasPoucoExperientes, aBackEndPraticasExperientes, aBackEndPraticasExperts), 4, byrow=T), ylim=c(0,100), xlim=c(0,35), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Back-end", legend.text=c("Inexperientes", "Pouco Experientes", "Experientes", "Experts"), col=topo.colors(4))

### Desenvolvedores Front-end
aFrontEndPraticas = c(nrow(ssFrontEndUsaModulo)/nFrontEnd100, nrow(ssFrontEndUsaPackageManager)/nFrontEnd100, nrow(ssFrontEndUsaAutomat)/nFrontEnd100, nrow(ssFrontEndFazTestes)/nFrontEnd100, nrow(ssFrontEndUsaContrVer)/nFrontEnd100, nrow(ssFrontEndUsaPreProCSS)/nFrontEnd100, nrow(ssFrontEndUsaFrameworkCSS)/nFrontEnd100, nrow(ssFrontEndUsaTemplateEng)/nFrontEnd100, nrow(ssFrontEndUsaOutraLing)/nFrontEnd100)
barplot(aFrontEndPraticas, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Front-end")

#### Dividido por Experiência

#### Inexperientes
aFrontEndPraticasInexperientes = c(nrow(ssFrontEndInexperienteUsaModulo)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteUsaPackageManager)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteUsaAutomat)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteFazTestes)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteUsaContrVer)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteUsaPreProCSS)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteUsaFrameworkCSS)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteUsaTemplateEng)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteUsaOutraLing)/nFrontEndInexperientes100)	
barplot(aFrontEndPraticasInexperientes, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Front-end Inexperientes")

#### Pouco Experientes
aFrontEndPraticasPoucoExperientes = c(nrow(ssFrontEndPoucoExperienteUsaModulo)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteUsaPackageManager)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteUsaAutomat)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteFazTestes)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteUsaContrVer)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteUsaPreProCSS)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteUsaFrameworkCSS)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteUsaTemplateEng)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteUsaOutraLing)/nFrontEndPoucoExperientes100)
barplot(aFrontEndPraticasPoucoExperientes, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Front-end Pouco Experientes")

#### Experientes
aFrontEndPraticasExperientes = c(nrow(ssFrontEndExperienteUsaModulo)/nFrontEndExperientes100, nrow(ssFrontEndExperienteUsaPackageManager)/nFrontEndExperientes100, nrow(ssFrontEndExperienteUsaAutomat)/nFrontEndExperientes100, nrow(ssFrontEndExperienteFazTestes)/nFrontEndExperientes100, nrow(ssFrontEndExperienteUsaContrVer)/nFrontEndExperientes100, nrow(ssFrontEndExperienteUsaPreProCSS)/nFrontEndExperientes100, nrow(ssFrontEndExperienteUsaFrameworkCSS)/nFrontEndExperientes100, nrow(ssFrontEndExperienteUsaTemplateEng)/nFrontEndExperientes100, nrow(ssFrontEndExperienteUsaOutraLing)/nFrontEndExperientes100)	
barplot(aFrontEndPraticasExperientes, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Front-end Experientes")

#### Experts
aFrontEndPraticasExperts = c(nrow(ssFrontEndExpertUsaModulo)/nFrontEndExperts100, nrow(ssFrontEndExpertUsaPackageManager)/nFrontEndExperts100, nrow(ssFrontEndExpertUsaAutomat)/nFrontEndExperts100, nrow(ssFrontEndExpertFazTestes)/nFrontEndExperts100, nrow(ssFrontEndExpertUsaContrVer)/nFrontEndExperts100, nrow(ssFrontEndExpertUsaPreProCSS)/nFrontEndExperts100, nrow(ssFrontEndExpertUsaFrameworkCSS)/nFrontEndExperts100, nrow(ssFrontEndExpertUsaTemplateEng)/nFrontEndExperts100, nrow(ssFrontEndExpertUsaOutraLing)/nFrontEndExperts100)
barplot(aFrontEndPraticasExperts, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Front-end Experts")

#### Comparando
barplot(matrix(c(aFrontEndPraticasInexperientes, aFrontEndPraticasPoucoExperientes, aFrontEndPraticasExperientes, aFrontEndPraticasExperts), 4, byrow=T), ylim=c(0,100), xlim=c(0,35), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Front-end", legend.text=c("Inexperientes", "Pouco Experientes", "Experientes", "Experts"), col=topo.colors(4))

### Front-end x Back-end
barplot(matrix(c(aBackEndPraticas, aFrontEndPraticas), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas", legend.text=c("Back-end", "Front-end"))

#### Dividido por Experiência

#### Inexperientes
barplot(matrix(c(aBackEndPraticasInexperientes, aFrontEndPraticasInexperientes), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas\nentre Inexperientes", legend.text=c("Back-end", "Front-end"))

#### Pouco Experientes	
barplot(matrix(c(aBackEndPraticasPoucoExperientes, aFrontEndPraticasPoucoExperientes), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas\nentre Pouco Experientes", legend.text=c("Back-end", "Front-end"))

#### Experientes
barplot(matrix(c(aBackEndPraticasExperientes, aFrontEndPraticasExperientes), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas\nentre Experientes", legend.text=c("Back-end", "Front-end"))

#### Experts
barplot(matrix(c(aBackEndPraticasExperts, aFrontEndPraticasExperts), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas\nentre experts", legend.text=c("Back-end", "Front-end"))


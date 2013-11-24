## Lê CSV
dados <- read.csv(file="respostas.csv",head=TRUE,sep=",")

## Apenas os que moram no Brasil

dados <- subset(dados, dados["BRA"] == "S")

## Condicionais

condFrontEnd = (dados["PER"] == "B" | dados["FOC"] == "S")
condBackEnd = (dados["PER"] == "A" & dados["FOC"] == "N")

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


## Front-end e práticas recentes da comunidade front-end
ssFrontEndUsaModulo <- subset(dados, condUsaModule & condFrontEnd)
ssFrontEndUsaPackageManager <- subset(dados, condUsaPackageManager & condFrontEnd)
ssFrontEndUsaAutomat <- subset(dados, condUsaAutomat & condFrontEnd)
ssFrontEndFazTestes <- subset(dados, condFazTestes & condFrontEnd)
ssFrontEndUsaContrVer <- subset(dados, condUsaContrVer & condFrontEnd)
ssFrontEndUsaPreProCSS <- subset(dados, condUsaPreProCSS & condFrontEnd)
ssFrontEndUsaFrameworkCSS <- subset(dados, condUsaFrameworkCSS & condFrontEnd)
ssFrontEndUsaTemplateEng <- subset(dados, condUsaTemplateEng & condFrontEnd)
ssFrontEndUsaOutraLing <- subset(dados, condUsaOutraLing & condFrontEnd)

# Variaveis

nBackEnd = nrow(ssBackEnd)
nBackEnd100 = nBackEnd / 100
nBackEndInexperientes = nrow(ssBackEndInexperientes) / nBackEnd100
nBackEndPoucoExperientes = nrow(ssBackEndPoucoExperientes) / nBackEnd100
nBackEndExperientes = nrow(ssBackEndExperientes) / nBackEnd100
nBackEndExperts = nrow(ssBackEndExperts) / nBackEnd100

nFrontEnd = nrow(ssFrontEnd)
nFrontEnd100 = nFrontEnd / 100
nFrontEndInexperientes = nrow(ssFrontEndInexperientes) / nFrontEnd100
nFrontEndPoucoExperientes = nrow(ssFrontEndPoucoExperientes) / nFrontEnd100
nFrontEndExperientes = nrow(ssFrontEndExperientes) / nFrontEnd100
nFrontEndExperts = nrow(ssFrontEndExperts) / nFrontEnd100

nDados = nrow(dados)
nDados100 = nDados / 100

cFerramPraticas =c("Module\nPattern", "Package\nManager", "Ferramenta\n de Automatizacao\nde Tarefas", "Testes", "Controle\nVersão", "Pré-processador\nCSS", "Framework CSS", "Template Engine", "Outra\nLinguagem para JS")

# Gráficos

### Comparação da Experiência em Front-end
aBackEndExp = c(nBackEndInexperientes, nBackEndPoucoExperientes, nBackEndExperientes, nBackEndExperts)
aFrontEndExp = c(nFrontEndInexperientes, nFrontEndPoucoExperientes, nFrontEndExperientes, nFrontEndExperts)
barplot(matrix(c(aBackEndExp, aFrontEndExp), 2, byrow=T), ylim=c(0,100), xlim=c(0,10), ylab="%", beside=T, space=c(0,0.2), density=5, angle=0, col=c("blue", "red"), names.arg=c("Inexperientes", "Pouco Experientes", "Experientes", "Experts"), main="Comparaçao\nda Experiência em Front-end", legend.text=c("Back-end", "Front-end"))

### Uso de Novas Ferramentas e Práticas Desenvolvedores Back-end
aBackEndPraticas = c(nrow(ssBackEndUsaModulo)/nBackEnd100, nrow(ssBackEndUsaPackageManager)/nBackEnd100, nrow(ssBackEndUsaAutomat)/nBackEnd100, nrow(ssBackEndFazTestes)/nBackEnd100, nrow(ssBackEndUsaContrVer)/nBackEnd100, nrow(ssBackEndUsaPreProCSS)/nBackEnd100, nrow(ssBackEndUsaFrameworkCSS)/nBackEnd100, nrow(ssBackEndUsaTemplateEng)/nBackEnd100, nrow(ssBackEndUsaOutraLing)/nBackEnd100)
barplot(aBackEndPraticas, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Back-end")

### Uso de Novas Ferramentas e Práticas Desenvolvedores Front-end
aFrontEndPraticas = c(nrow(ssFrontEndUsaModulo)/nFrontEnd100, nrow(ssFrontEndUsaPackageManager)/nFrontEnd100, nrow(ssFrontEndUsaAutomat)/nFrontEnd100, nrow(ssFrontEndFazTestes)/nFrontEnd100, nrow(ssFrontEndUsaContrVer)/nFrontEnd100, nrow(ssFrontEndUsaPreProCSS)/nFrontEnd100, nrow(ssFrontEndUsaFrameworkCSS)/nFrontEnd100, nrow(ssFrontEndUsaTemplateEng)/nFrontEnd100, nrow(ssFrontEndUsaOutraLing)/nFrontEnd100)
barplot(aFrontEndPraticas, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Front-end")

### Comparação do Uso de Novas Ferramentas e Práticas
barplot(matrix(c(aBackEndPraticas, aFrontEndPraticas), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas", legend.text=c("Back-end", "Front-end"))

### Comparação do Uso de Novas Ferramentas e Práticas por Experiência

#### Comparação do Uso de Novas Ferramentas e Práticas de Inexperientes


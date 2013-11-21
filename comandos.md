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

# Variaveis

nBackEnd = nrow(ssBackEnd)
nFrontEnd = nrow(ssFrontEnd)
nDados = nrow(dados)
nDados100 = nDados / 100

# Gráficos

### Comparação da Experiência em Front-end
aBackEndExp = c(nrow(ssBackEndInexperientes)/nDados100, nrow(ssBackEndPoucoExperientes)/nDados100, nrow(ssBackEndExperientes)/nDados100, nrow(ssBackEndExperts)/nDados100)
aFrontEndExp = c(nrow(ssFrontEndInexperientes)/nDados100, nrow(ssFrontEndPoucoExperientes)/nDados100, nrow(ssFrontEndExperientes)/nDados100, nrow(ssFrontEndExperts)/nDados100)
barplot(matrix(c(aBackEndExp, aFrontEndExp), 2), ylim=c(0,50), xlim=c(0,10), beside=T, space=c(0,0.2), names.arg=c("Inexperientes", "Pouco Experientes", "Experientes", "Experts"), ylab="%", main="Comparaçao da Experiência em Front-end", legend.text=c("Back-end", "Front-end"))
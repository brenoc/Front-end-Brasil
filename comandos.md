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
condNaoUsaFrameworkJS = (is.na(dados["FRW.ANG"]) & is.na(dados["FRW.BBO"]) & is.na(dados["FRW.EMB"]) & is.na(dados["FRW.KNO"]) & is.na(dados["FRW.OTH"]) & is.na(dados["FRW.JQU"]))

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

condMinHTML = (dados["PRO.MHT"] == 1)
condNaoMinHTML = (is.na(dados["PRO.MHT"]))

condMinCSS = (dados["PRO.MCS"] == 1)
condNaoMinCSS = (is.na(dados["PRO.MCS"]))

condMinJS = (dados["PRO.MJS"] == 1)
condNaoMinJS = (is.na(dados["PRO.MJS"]))

condComCSS = (dados["PRO.CCS"] == 1)
condNaoComCSS = (is.na(dados["PRO.CCS"]))

condComJS = (dados["PRO.CJS"] == 1)
condNaoComJS = (is.na(dados["PRO.CJS"]))

condOtim = (dados["PRO.OIM"] == 1)
condNaoOtim = (is.na(dados["PRO.OIM"]))

condCDNpu = (dados["PRO.CDU"] == 1)
condNaoCDNpu = (is.na(dados["PRO.CDU"]))

condCDNpr = (dados["PRO.CDR"] == 1)
condNaoCDNpr = (is.na(dados["PRO.CDR"]))

condEditSub = (dados["EDT.SUB"] == 1)
condEditWeb = (dados["EDT.WEB"] == 1)
condEditNot = (dados["EDT.NOT"] == 1)
condEditVst = (dados["EDT.VST"] == 1)
condEditDrw = (dados["EDT.DRW"] == 1)
condEditVim = (dados["EDT.VIM"] == 1)
condEditEma = (dados["EDT.EMA"] == 1)
condEditTxm = (dados["EDT.TXM"] == 1)
condEditNet = (dados["EDT.NET"] == 1)
condEditEcl = (dados["EDT.ECL"] == 1)
condEditBra = (dados["EDT.BRA"] == 1)
condEditOth = (dados["EDT.OTH"] == 1)

## Subsets

## Perfis
ssBackEnd <- subset(dados, condBackEnd)
ssFrontEnd <- subset(dados, condFrontEnd)

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

## Frameworks JS
ssBackEndFrameworksJS <- subset(dados, condUsaFrameworksJS & condBackEnd)
ssBackEndSoJquery <- subset(dados, condUsaApenasJquery & condBackEnd)
ssBackEndNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condBackEnd)
ssFrontEndFrameworksJS <- subset(dados, condUsaFrameworksJS & condFrontEnd)
ssFrontEndSoJquery <- subset(dados, condUsaApenasJquery & condFrontEnd)
ssFrontEndNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condFrontEnd)

	#### Divido por Experiência

	ssBackEndInexperienteFrameworkJS <- subset(dados, condUsaFrameworksJS & condInexperientes & condBackEnd)
	ssBackEndInexperienteSoJquery <- subset(dados, condUsaApenasJquery & condInexperientes & condBackEnd)
	ssBackEndInexperienteNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condInexperientes & condBackEnd)
	ssBackEndPoucoExperienteFrameworkJS <- subset(dados, condUsaFrameworksJS & condPoucoExperientes & condBackEnd)
	ssBackEndPoucoExperienteSoJquery <- subset(dados, condUsaApenasJquery & condPoucoExperientes & condBackEnd)
	ssBackEndPoucoExperienteNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condPoucoExperientes & condBackEnd)
	ssBackEndExperienteFrameworkJS <- subset(dados, condUsaFrameworksJS & condExperientes & condBackEnd)
	ssBackEndExperienteSoJquery <- subset(dados, condUsaApenasJquery & condExperientes & condBackEnd)
	ssBackEndExperienteNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condExperientes & condBackEnd)
	ssBackEndExpertsFrameworkJS <- subset(dados, condUsaFrameworksJS & condExperts & condBackEnd)
	ssBackEndExpertsSoJquery <- subset(dados, condUsaApenasJquery & condExperts & condBackEnd)
	ssBackEndExpertsNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condExperts & condBackEnd)

	ssFrontEndInexperienteFrameworkJS <- subset(dados, condUsaFrameworksJS & condInexperientes & condFrontEnd)
	ssFrontEndInexperienteSoJquery <- subset(dados, condUsaApenasJquery & condInexperientes & condFrontEnd)
	ssFrontEndInexperienteNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condInexperientes & condFrontEnd)
	ssFrontEndPoucoExperienteFrameworkJS <- subset(dados, condUsaFrameworksJS & condPoucoExperientes & condFrontEnd)
	ssFrontEndPoucoExperienteSoJquery <- subset(dados, condUsaApenasJquery & condPoucoExperientes & condFrontEnd)
	ssFrontEndPoucoExperienteNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condPoucoExperientes & condFrontEnd)
	ssFrontEndExperienteFrameworkJS <- subset(dados, condUsaFrameworksJS & condExperientes & condFrontEnd)
	ssFrontEndExperienteSoJquery <- subset(dados, condUsaApenasJquery & condExperientes & condFrontEnd)
	ssFrontEndExperienteNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condExperientes & condFrontEnd)
	ssFrontEndExpertsFrameworkJS <- subset(dados, condUsaFrameworksJS & condExperts & condFrontEnd)
	ssFrontEndExpertsSoJquery <- subset(dados, condUsaApenasJquery & condExperts & condFrontEnd)
	ssFrontEndExpertsNaoFrameworkJS <- subset(dados, condNaoUsaFrameworkJS & condExperts & condFrontEnd)

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

## Processos

	### Back-end
	ssBackEndMinHTML <- subset(dados, condMinHTML & condBackEnd)
	ssBackEndMinCSS <- subset(dados, condMinCSS & condBackEnd)
	ssBackEndMinJS <- subset(dados, condMinJS & condBackEnd)
	ssBackEndComCSS <- subset(dados, condComCSS & condBackEnd)
	ssBackEndComJS <- subset(dados, condComJS & condBackEnd)
	ssBackEndOtim <- subset(dados, condOtim & condBackEnd)
	ssBackEndCDNpu <- subset(dados, condCDNpu & condBackEnd)
	ssBackEndCDNpr <- subset(dados, condCDNpr & condBackEnd)

		#### Divido por Experiência

		##### Inexperientes
		ssBackEndInexperienteMinHTML <- subset(dados, condMinHTML & condInexperientes & condBackEnd)
		ssBackEndInexperienteMinCSS <- subset(dados, condMinCSS & condInexperientes & condBackEnd)
		ssBackEndInexperienteMinJS <- subset(dados, condMinJS & condInexperientes & condBackEnd)
		ssBackEndInexperienteComCSS <- subset(dados, condComCSS & condInexperientes & condBackEnd)
		ssBackEndInexperienteComJS <- subset(dados, condComJS & condInexperientes & condBackEnd)
		ssBackEndInexperienteOtim <- subset(dados, condOtim & condInexperientes & condBackEnd)
		ssBackEndInexperienteCDNpu <- subset(dados, condCDNpu & condInexperientes & condBackEnd)
		ssBackEndInexperienteCDNpr <- subset(dados, condCDNpr & condInexperientes & condBackEnd)

		##### Pouco Experientes
		ssBackEndPoucoExperienteMinHTML <- subset(dados, condMinHTML & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteMinCSS <- subset(dados, condMinCSS & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteMinJS <- subset(dados, condMinJS & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteComCSS <- subset(dados, condComCSS & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteComJS <- subset(dados, condComJS & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteOtim <- subset(dados, condOtim & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteCDNpu <- subset(dados, condCDNpu & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteCDNpr <- subset(dados, condCDNpr & condPoucoExperientes & condBackEnd)

		##### Experientes
		ssBackEndExperienteMinHTML <- subset(dados, condMinHTML & condExperientes & condBackEnd)
		ssBackEndExperienteMinCSS <- subset(dados, condMinCSS & condExperientes & condBackEnd)
		ssBackEndExperienteMinJS <- subset(dados, condMinJS & condExperientes & condBackEnd)
		ssBackEndExperienteComCSS <- subset(dados, condComCSS & condExperientes & condBackEnd)
		ssBackEndExperienteComJS <- subset(dados, condComJS & condExperientes & condBackEnd)
		ssBackEndExperienteOtim <- subset(dados, condOtim & condExperientes & condBackEnd)
		ssBackEndExperienteCDNpu <- subset(dados, condCDNpu & condExperientes & condBackEnd)
		ssBackEndExperienteCDNpr <- subset(dados, condCDNpr & condExperientes & condBackEnd)

		##### Experts
		ssBackEndExpertMinHTML <- subset(dados, condMinHTML & condExperts & condBackEnd)
		ssBackEndExpertMinCSS <- subset(dados, condMinCSS & condExperts & condBackEnd)
		ssBackEndExpertMinJS <- subset(dados, condMinJS & condExperts & condBackEnd)
		ssBackEndExpertComCSS <- subset(dados, condComCSS & condExperts & condBackEnd)
		ssBackEndExpertComJS <- subset(dados, condComJS & condExperts & condBackEnd)
		ssBackEndExpertOtim <- subset(dados, condOtim & condExperts & condBackEnd)
		ssBackEndExpertCDNpu <- subset(dados, condCDNpu & condExperts & condBackEnd)
		ssBackEndExpertCDNpr <- subset(dados, condCDNpr & condExperts & condBackEnd)

	### Front-end
	ssFrontEndMinHTML <- subset(dados, condMinHTML & condFrontEnd)
	ssFrontEndMinCSS <- subset(dados, condMinCSS & condFrontEnd)
	ssFrontEndMinJS <- subset(dados, condMinJS & condFrontEnd)
	ssFrontEndComCSS <- subset(dados, condComCSS & condFrontEnd)
	ssFrontEndComJS <- subset(dados, condComJS & condFrontEnd)
	ssFrontEndOtim <- subset(dados, condOtim & condFrontEnd)
	ssFrontEndCDNpu <- subset(dados, condCDNpu & condFrontEnd)
	ssFrontEndCDNpr <- subset(dados, condCDNpr & condFrontEnd)

		#### Divido por Experiência

		##### Inexperientes
		ssFrontEndInexperienteMinHTML <- subset(dados, condMinHTML & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteMinCSS <- subset(dados, condMinCSS & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteMinJS <- subset(dados, condMinJS & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteComCSS <- subset(dados, condComCSS & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteComJS <- subset(dados, condComJS & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteOtim <- subset(dados, condOtim & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteCDNpu <- subset(dados, condCDNpu & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteCDNpr <- subset(dados, condCDNpr & condInexperientes & condFrontEnd)

		##### Pouco Experientes
		ssFrontEndPoucoExperienteMinHTML <- subset(dados, condMinHTML & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteMinCSS <- subset(dados, condMinCSS & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteMinJS <- subset(dados, condMinJS & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteComCSS <- subset(dados, condComCSS & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteComJS <- subset(dados, condComJS & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteOtim <- subset(dados, condOtim & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteCDNpu <- subset(dados, condCDNpu & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteCDNpr <- subset(dados, condCDNpr & condPoucoExperientes & condFrontEnd)

		##### Experientes
		ssFrontEndExperienteMinHTML <- subset(dados, condMinHTML & condExperientes & condFrontEnd)
		ssFrontEndExperienteMinCSS <- subset(dados, condMinCSS & condExperientes & condFrontEnd)
		ssFrontEndExperienteMinJS <- subset(dados, condMinJS & condExperientes & condFrontEnd)
		ssFrontEndExperienteComCSS <- subset(dados, condComCSS & condExperientes & condFrontEnd)
		ssFrontEndExperienteComJS <- subset(dados, condComJS & condExperientes & condFrontEnd)
		ssFrontEndExperienteOtim <- subset(dados, condOtim & condExperientes & condFrontEnd)
		ssFrontEndExperienteCDNpu <- subset(dados, condCDNpu & condExperientes & condFrontEnd)
		ssFrontEndExperienteCDNpr <- subset(dados, condCDNpr & condExperientes & condFrontEnd)

		##### Experts
		ssFrontEndExpertMinHTML <- subset(dados, condMinHTML & condExperts & condFrontEnd)
		ssFrontEndExpertMinCSS <- subset(dados, condMinCSS & condExperts & condFrontEnd)
		ssFrontEndExpertMinJS <- subset(dados, condMinJS & condExperts & condFrontEnd)
		ssFrontEndExpertComCSS <- subset(dados, condComCSS & condExperts & condFrontEnd)
		ssFrontEndExpertComJS <- subset(dados, condComJS & condExperts & condFrontEnd)
		ssFrontEndExpertOtim <- subset(dados, condOtim & condExperts & condFrontEnd)
		ssFrontEndExpertCDNpu <- subset(dados, condCDNpu & condExperts & condFrontEnd)
		ssFrontEndExpertCDNpr <- subset(dados, condCDNpr & condExperts & condFrontEnd)

## Editor de Texto

	### Back-end
	ssBackEndEditSub <- subset(dados, condEditSub & condBackEnd)
	ssBackEndEditWeb <- subset(dados, condEditWeb & condBackEnd)
	ssBackEndEditNot <- subset(dados, condEditNot & condBackEnd)
	ssBackEndEditVst <- subset(dados, condEditVst & condBackEnd)
	ssBackEndEditDrw <- subset(dados, condEditDrw & condBackEnd)
	ssBackEndEditVim <- subset(dados, condEditVim & condBackEnd)
	ssBackEndEditEma <- subset(dados, condEditEma & condBackEnd)
	ssBackEndEditTxm <- subset(dados, condEditTxm & condBackEnd)
	ssBackEndEditNet <- subset(dados, condEditNet & condBackEnd)
	ssBackEndEditEcl <- subset(dados, condEditEcl & condBackEnd)
	ssBackEndEditBra <- subset(dados, condEditBra & condBackEnd)
	ssBackEndEditOth <- subset(dados, condEditOth & condBackEnd)

		#### Divido por Experiência

		##### Inexperientes
		ssBackEndInexperienteEditSub <- subset(dados, condEditSub & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditWeb <- subset(dados, condEditWeb & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditNot <- subset(dados, condEditNot & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditVst <- subset(dados, condEditVst & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditDrw <- subset(dados, condEditDrw & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditVim <- subset(dados, condEditVim & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditEma <- subset(dados, condEditEma & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditTxm <- subset(dados, condEditTxm & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditNet <- subset(dados, condEditNet & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditEcl <- subset(dados, condEditEcl & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditBra <- subset(dados, condEditBra & condInexperientes & condBackEnd)
		ssBackEndInexperienteEditOth <- subset(dados, condEditOth & condInexperientes & condBackEnd)

		##### Pouco Experientes
		ssBackEndPoucoExperienteEditSub <- subset(dados, condEditSub & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditWeb <- subset(dados, condEditWeb & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditNot <- subset(dados, condEditNot & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditVst <- subset(dados, condEditVst & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditDrw <- subset(dados, condEditDrw & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditVim <- subset(dados, condEditVim & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditEma <- subset(dados, condEditEma & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditTxm <- subset(dados, condEditTxm & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditNet <- subset(dados, condEditNet & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditEcl <- subset(dados, condEditEcl & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditBra <- subset(dados, condEditBra & condPoucoExperientes & condBackEnd)
		ssBackEndPoucoExperienteEditOth <- subset(dados, condEditOth & condPoucoExperientes & condBackEnd)

		##### Experientes
		ssBackEndExperienteEditSub <- subset(dados, condEditSub & condExperientes & condBackEnd)
		ssBackEndExperienteEditWeb <- subset(dados, condEditWeb & condExperientes & condBackEnd)
		ssBackEndExperienteEditNot <- subset(dados, condEditNot & condExperientes & condBackEnd)
		ssBackEndExperienteEditVst <- subset(dados, condEditVst & condExperientes & condBackEnd)
		ssBackEndExperienteEditDrw <- subset(dados, condEditDrw & condExperientes & condBackEnd)
		ssBackEndExperienteEditVim <- subset(dados, condEditVim & condExperientes & condBackEnd)
		ssBackEndExperienteEditEma <- subset(dados, condEditEma & condExperientes & condBackEnd)
		ssBackEndExperienteEditTxm <- subset(dados, condEditTxm & condExperientes & condBackEnd)
		ssBackEndExperienteEditNet <- subset(dados, condEditNet & condExperientes & condBackEnd)
		ssBackEndExperienteEditEcl <- subset(dados, condEditEcl & condExperientes & condBackEnd)
		ssBackEndExperienteEditBra <- subset(dados, condEditBra & condExperientes & condBackEnd)
		ssBackEndExperienteEditOth <- subset(dados, condEditOth & condExperientes & condBackEnd)

		##### Experts
		ssBackEndExpertEditSub <- subset(dados, condEditSub & condExperts & condBackEnd)
		ssBackEndExpertEditWeb <- subset(dados, condEditWeb & condExperts & condBackEnd)
		ssBackEndExpertEditNot <- subset(dados, condEditNot & condExperts & condBackEnd)
		ssBackEndExpertEditVst <- subset(dados, condEditVst & condExperts & condBackEnd)
		ssBackEndExpertEditDrw <- subset(dados, condEditDrw & condExperts & condBackEnd)
		ssBackEndExpertEditVim <- subset(dados, condEditVim & condExperts & condBackEnd)
		ssBackEndExpertEditEma <- subset(dados, condEditEma & condExperts & condBackEnd)
		ssBackEndExpertEditTxm <- subset(dados, condEditTxm & condExperts & condBackEnd)
		ssBackEndExpertEditNet <- subset(dados, condEditNet & condExperts & condBackEnd)
		ssBackEndExpertEditEcl <- subset(dados, condEditEcl & condExperts & condBackEnd)
		ssBackEndExpertEditBra <- subset(dados, condEditBra & condExperts & condBackEnd)
		ssBackEndExpertEditOth <- subset(dados, condEditOth & condExperts & condBackEnd)

	### Front-end
	ssFrontEndEditSub <- subset(dados, condEditSub & condFrontEnd)
	ssFrontEndEditWeb <- subset(dados, condEditWeb & condFrontEnd)
	ssFrontEndEditNot <- subset(dados, condEditNot & condFrontEnd)
	ssFrontEndEditVst <- subset(dados, condEditVst & condFrontEnd)
	ssFrontEndEditDrw <- subset(dados, condEditDrw & condFrontEnd)
	ssFrontEndEditVim <- subset(dados, condEditVim & condFrontEnd)
	ssFrontEndEditEma <- subset(dados, condEditEma & condFrontEnd)
	ssFrontEndEditTxm <- subset(dados, condEditTxm & condFrontEnd)
	ssFrontEndEditNet <- subset(dados, condEditNet & condFrontEnd)
	ssFrontEndEditEcl <- subset(dados, condEditEcl & condFrontEnd)
	ssFrontEndEditBra <- subset(dados, condEditBra & condFrontEnd)
	ssFrontEndEditOth <- subset(dados, condEditOth & condFrontEnd)

		#### Divido por Experiência

		##### Inexperientes
		ssFrontEndInexperienteEditSub <- subset(dados, condEditSub & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditWeb <- subset(dados, condEditWeb & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditNot <- subset(dados, condEditNot & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditVst <- subset(dados, condEditVst & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditDrw <- subset(dados, condEditDrw & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditVim <- subset(dados, condEditVim & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditEma <- subset(dados, condEditEma & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditTxm <- subset(dados, condEditTxm & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditNet <- subset(dados, condEditNet & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditEcl <- subset(dados, condEditEcl & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditBra <- subset(dados, condEditBra & condInexperientes & condFrontEnd)
		ssFrontEndInexperienteEditOth <- subset(dados, condEditOth & condInexperientes & condFrontEnd)

		##### Pouco Experientes
		ssFrontEndPoucoExperienteEditSub <- subset(dados, condEditSub & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditWeb <- subset(dados, condEditWeb & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditNot <- subset(dados, condEditNot & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditVst <- subset(dados, condEditVst & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditDrw <- subset(dados, condEditDrw & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditVim <- subset(dados, condEditVim & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditEma <- subset(dados, condEditEma & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditTxm <- subset(dados, condEditTxm & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditNet <- subset(dados, condEditNet & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditEcl <- subset(dados, condEditEcl & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditBra <- subset(dados, condEditBra & condPoucoExperientes & condFrontEnd)
		ssFrontEndPoucoExperienteEditOth <- subset(dados, condEditOth & condPoucoExperientes & condFrontEnd)

		##### Experientes
		ssFrontEndExperienteEditSub <- subset(dados, condEditSub & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditWeb <- subset(dados, condEditWeb & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditNot <- subset(dados, condEditNot & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditVst <- subset(dados, condEditVst & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditDrw <- subset(dados, condEditDrw & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditVim <- subset(dados, condEditVim & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditEma <- subset(dados, condEditEma & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditTxm <- subset(dados, condEditTxm & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditNet <- subset(dados, condEditNet & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditEcl <- subset(dados, condEditEcl & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditBra <- subset(dados, condEditBra & condExperientes & condFrontEnd)
		ssFrontEndExperienteEditOth <- subset(dados, condEditOth & condExperientes & condFrontEnd)

		##### Experts
		ssFrontEndExpertEditSub <- subset(dados, condEditSub & condExperts & condFrontEnd)
		ssFrontEndExpertEditWeb <- subset(dados, condEditWeb & condExperts & condFrontEnd)
		ssFrontEndExpertEditNot <- subset(dados, condEditNot & condExperts & condFrontEnd)
		ssFrontEndExpertEditVst <- subset(dados, condEditVst & condExperts & condFrontEnd)
		ssFrontEndExpertEditDrw <- subset(dados, condEditDrw & condExperts & condFrontEnd)
		ssFrontEndExpertEditVim <- subset(dados, condEditVim & condExperts & condFrontEnd)
		ssFrontEndExpertEditEma <- subset(dados, condEditEma & condExperts & condFrontEnd)
		ssFrontEndExpertEditTxm <- subset(dados, condEditTxm & condExperts & condFrontEnd)
		ssFrontEndExpertEditNet <- subset(dados, condEditNet & condExperts & condFrontEnd)
		ssFrontEndExpertEditEcl <- subset(dados, condEditEcl & condExperts & condFrontEnd)
		ssFrontEndExpertEditBra <- subset(dados, condEditBra & condExperts & condFrontEnd)
		ssFrontEndExpertEditOth <- subset(dados, condEditOth & condExperts & condFrontEnd)

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

cFerramPraticas = c("Module\nPattern", "Package\nManager", "Ferramenta\n de Automatizacao\nde Tarefas", "Testes", "Controle\nVersão", "Pré-processador\nCSS", "Framework CSS", "Template Engine", "Outra\nLinguagem para JS")
cProcessos = c("Minifica HTML","Minifica CSS","Minifica JS","Concatena CSS","Concatena JS","Otimiza\nas imagens","Serve em\nCDN público","Serve em\nCDN próprio")
cExperiencias = c("Inexperientes", "Pouco Experientes", "Experientes", "Experts")
cEditores = c("Sublime Text", "JetBrains", "Notepad++", "Visual Studio", "Dreamweaver", "VI / VIM", "Emacs", "TextMate", "NetBeans", "Eclipse", "Brackets", "Other")

# Gráficos

### Comparação da Experiência em Front-end
aBackEndExp = c(nBackEndInexperientes / nBackEnd100, nBackEndPoucoExperientes / nBackEnd100, nBackEndExperientes / nBackEnd100, nBackEndExperts / nBackEnd100)
aFrontEndExp = c(nFrontEndInexperientes / nFrontEnd100, nFrontEndPoucoExperientes / nFrontEnd100, nFrontEndExperientes / nFrontEnd100, nFrontEndExperts / nFrontEnd100)
barplot(matrix(c(aBackEndExp, aFrontEndExp), 2, byrow=T), ylim=c(0,100), xlim=c(0,10), ylab="%", beside=T, space=c(0,0.2), density=5, angle=0, col=c("blue", "red"), names.arg=cExperiencias, main="Comparaçao\nda Experiência em Front-end", legend.text=c("Back-end", "Front-end"))


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
			barplot(matrix(c(aBackEndPraticasInexperientes, aBackEndPraticasPoucoExperientes, aBackEndPraticasExperientes, aBackEndPraticasExperts), 4, byrow=T), ylim=c(0,100), xlim=c(0,35), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Back-end", legend.text=cExperiencias, col=topo.colors(4))

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
			barplot(matrix(c(aFrontEndPraticasInexperientes, aFrontEndPraticasPoucoExperientes, aFrontEndPraticasExperientes, aFrontEndPraticasExperts), 4, byrow=T), ylim=c(0,100), xlim=c(0,35), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, names.arg=cFerramPraticas, main="Uso de Novas Ferramentas e Práticas\nDesenvolvedores Front-end", legend.text=cExperiencias, col=topo.colors(4))

	### Comparação Front-end x Back-end
	barplot(matrix(c(aBackEndPraticas, aFrontEndPraticas), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas", legend.text=c("Back-end", "Front-end"))

		#### Dividido por Experiência

			#### Inexperientes
			barplot(matrix(c(aBackEndPraticasInexperientes, aFrontEndPraticasInexperientes), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas\nentre Inexperientes", legend.text=c("Back-end", "Front-end"))

			#### Pouco Experientes	
			barplot(matrix(c(aBackEndPraticasPoucoExperientes, aFrontEndPraticasPoucoExperientes), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas\nentre Pouco Experientes", legend.text=c("Back-end", "Front-end"))

			#### Experientes
			barplot(matrix(c(aBackEndPraticasExperientes, aFrontEndPraticasExperientes), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas\nentre Experientes", legend.text=c("Back-end", "Front-end"))

			#### Experts
			barplot(matrix(c(aBackEndPraticasExperts, aFrontEndPraticasExperts), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas\nentre Experts", legend.text=c("Back-end", "Front-end"))

## Uso de Framework JS

	pFrameworkJS = barplot(mFrameworkJS, ylim=c(0,100), xlim=c(0,5), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=c("Apenas jQuery", "Outros\nFrameworks JS"), main="Comparação\ndo Uso de Frameworks Javascript", legend.text=c("Back-end", "Front-end"))

	### Back-end
	barplot(matrix(c(nrow(ssBackEndInexperienteSoJquery)/nBackEndInexperientes100, nrow(ssBackEndInexperienteFrameworkJS)/nBackEndInexperientes100, nrow(ssBackEndInexperienteNaoFrameworkJS)/nBackEndInexperientes100, nrow(ssBackEndPoucoExperienteSoJquery)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteFrameworkJS)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteNaoFrameworkJS)/nBackEndPoucoExperientes100, nrow(ssBackEndExperienteSoJquery)/nBackEndExperientes100, nrow(ssBackEndExperienteFrameworkJS)/nBackEndExperientes100, nrow(ssBackEndExperienteNaoFrameworkJS)/nBackEndExperientes100, nrow(ssBackEndExpertsSoJquery)/nBackEndExperts100, nrow(ssBackEndExpertsFrameworkJS)/nBackEndExperts100, nrow(ssBackEndExpertsNaoFrameworkJS)/nBackEndExperts100), 3, byrow=F), ylim=c(0,100), xlim=c(0,8), ylab="%", density=5, angle=0, cex.names=0.7, beside=F, col=topo.colors(3), legend.text=c("Apenas jQuery", "Outros Frameworks JS", "Não usa"), main="Back-end\nUso de Frameworks Javascript", names.arg=cExperiencias)

	### Front-end
	barplot(matrix(c(nrow(ssFrontEndInexperienteSoJquery)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteFrameworkJS)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteNaoFrameworkJS)/nFrontEndInexperientes100, nrow(ssFrontEndPoucoExperienteSoJquery)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteFrameworkJS)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteNaoFrameworkJS)/nFrontEndPoucoExperientes100, nrow(ssFrontEndExperienteSoJquery)/nFrontEndExperientes100, nrow(ssFrontEndExperienteFrameworkJS)/nFrontEndExperientes100, nrow(ssFrontEndExperienteNaoFrameworkJS)/nFrontEndExperientes100, nrow(ssFrontEndExpertsSoJquery)/nFrontEndExperts100, nrow(ssFrontEndExpertsFrameworkJS)/nFrontEndExperts100, nrow(ssFrontEndExpertsNaoFrameworkJS)/nFrontEndExperts100), 3, byrow=F), ylim=c(0,100), xlim=c(0,8), ylab="%", density=5, angle=0, cex.names=0.7, beside=F, col=topo.colors(3), legend.text=c("Apenas jQuery", "Outros Frameworks JS", "Não usa"), main="Front-end\nUso de Frameworks Javascript", names.arg=cExperiencias)

	### Divido por Experiência
	
	aBackEndSoJqueryExp = c(nrow(ssBackEndInexperienteSoJquery)/nBackEndInexperientes100, nrow(ssBackEndPoucoExperienteSoJquery)/nBackEndPoucoExperientes100, nrow(ssBackEndExperienteSoJquery)/nBackEndExperientes100, nrow(ssBackEndExpertsSoJquery)/nBackEndExperts100)
	aFrontEndSoJqueryExp = c(nrow(ssFrontEndInexperienteSoJquery)/nFrontEndInexperientes100, nrow(ssFrontEndPoucoExperienteSoJquery)/nFrontEndPoucoExperientes100, nrow(ssFrontEndExperienteSoJquery)/nFrontEndExperientes100, nrow(ssFrontEndExpertsSoJquery)/nFrontEndExperts100)	
	barplot(matrix(c(aBackEndSoJqueryExp, aFrontEndSoJqueryExp), 2, byrow=T), ylim=c(0,100), xlim=c(0,10), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), legend.text=c("Back-end", "Front-end"), names.arg=cExperiencias, main="Uso de Apenas jQuery")

	aBackEndFrameworkJSExp = c(nrow(ssBackEndInexperienteFrameworkJS)/nBackEndInexperientes100, nrow(ssBackEndPoucoExperienteFrameworkJS)/nBackEndPoucoExperientes100, nrow(ssBackEndExperienteFrameworkJS)/nBackEndExperientes100, nrow(ssBackEndExpertsFrameworkJS)/nBackEndExperts100)
	aFrontEndFrameworkJSExp = c(nrow(ssFrontEndInexperienteFrameworkJS)/nFrontEndInexperientes100, nrow(ssFrontEndPoucoExperienteFrameworkJS)/nFrontEndPoucoExperientes100, nrow(ssFrontEndExperienteFrameworkJS)/nFrontEndExperientes100, nrow(ssFrontEndExpertsFrameworkJS)/nFrontEndExperts100)	
	barplot(matrix(c(aBackEndFrameworkJSExp, aFrontEndFrameworkJSExp), 2, byrow=T), ylim=c(0,100), xlim=c(0,10), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), legend.text=c("Back-end", "Front-end"), names.arg=cExperiencias, main="Uso de Outros Frameworks Javascript")

## Processos
	
	### Desenvolvedores Back-end
	aBackEndProcessos = c(nrow(ssBackEndMinHTML)/nBackEnd100, nrow(ssBackEndMinCSS)/nBackEnd100, nrow(ssBackEndMinJS)/nBackEnd100, nrow(ssBackEndComCSS)/nBackEnd100, nrow(ssBackEndComJS)/nBackEnd100, nrow(ssBackEndOtim)/nBackEnd100, nrow(ssBackEndCDNpu)/nBackEnd100, nrow(ssBackEndCDNpr)/nBackEnd100)
	barplot(aBackEndProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Back-end")

	#### Dividido por Experiência

		#### Inexperientes
		aBackEndProcessosInexperiente = c(nrow(ssBackEndInexperienteMinHTML)/nBackEndInexperientes100, nrow(ssBackEndInexperienteMinCSS)/nBackEndInexperientes100, nrow(ssBackEndInexperienteMinJS)/nBackEndInexperientes100, nrow(ssBackEndInexperienteComCSS)/nBackEndInexperientes100, nrow(ssBackEndInexperienteComJS)/nBackEndInexperientes100, nrow(ssBackEndInexperienteOtim)/nBackEndInexperientes100, nrow(ssBackEndInexperienteCDNpu)/nBackEndInexperientes100, nrow(ssBackEndInexperienteCDNpr)/nBackEndInexperientes100)
		barplot(aBackEndInexperienteProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Back-end Inexperientes")

		#### Pouco Experientes
		aBackEndProcessosPoucoExperiente = c(nrow(ssBackEndPoucoExperienteMinHTML)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteMinCSS)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteMinJS)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteComCSS)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteComJS)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteOtim)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteCDNpu)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteCDNpr)/nBackEndPoucoExperientes100)
		barplot(aBackEndPoucoExperienteProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Back-end Pouco Experientes")

		#### Experientes
		aBackEndProcessosExperiente = c(nrow(ssBackEndExperienteMinHTML)/nBackEndExperientes100, nrow(ssBackEndExperienteMinCSS)/nBackEndExperientes100, nrow(ssBackEndExperienteMinJS)/nBackEndExperientes100, nrow(ssBackEndExperienteComCSS)/nBackEndExperientes100, nrow(ssBackEndExperienteComJS)/nBackEndExperientes100, nrow(ssBackEndExperienteOtim)/nBackEndExperientes100, nrow(ssBackEndExperienteCDNpu)/nBackEndExperientes100, nrow(ssBackEndExperienteCDNpr)/nBackEndExperientes100)
		barplot(aBackEndExperienteProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Back-end Experientes")

		#### Experts
		aBackEndProcessosExpert = c(nrow(ssBackEndExpertMinHTML)/nBackEndExperts100, nrow(ssBackEndExpertMinCSS)/nBackEndExperts100, nrow(ssBackEndExpertMinJS)/nBackEndExperts100, nrow(ssBackEndExpertComCSS)/nBackEndExperts100, nrow(ssBackEndExpertComJS)/nBackEndExperts100, nrow(ssBackEndExpertOtim)/nBackEndExperts100, nrow(ssBackEndExpertCDNpu)/nBackEndExperts100, nrow(ssBackEndExpertCDNpr)/nBackEndExperts100)
		barplot(aBackEndExpertProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Back-end Pouco Experts")

	### Desenvolvedores Front-end
	aFrontEndProcessos = c(nrow(ssFrontEndMinHTML)/nFrontEnd100, nrow(ssFrontEndMinCSS)/nFrontEnd100, nrow(ssFrontEndMinJS)/nFrontEnd100, nrow(ssFrontEndComCSS)/nFrontEnd100, nrow(ssFrontEndComJS)/nFrontEnd100, nrow(ssFrontEndOtim)/nFrontEnd100, nrow(ssFrontEndCDNpu)/nFrontEnd100, nrow(ssFrontEndCDNpr)/nFrontEnd100)
	barplot(aFrontEndProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Front-end")

	#### Dividido por Experiência

		#### Inexperientes
		aFrontEndProcessosInexperiente = c(nrow(ssFrontEndInexperienteMinHTML)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteMinCSS)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteMinJS)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteComCSS)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteComJS)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteOtim)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteCDNpu)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteCDNpr)/nFrontEndInexperientes100)
		barplot(aFrontEndInexperienteProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Front-end Inexperientes")

		#### Pouco Experientes
		aFrontEndProcessosPoucoExperiente = c(nrow(ssFrontEndPoucoExperienteMinHTML)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteMinCSS)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteMinJS)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteComCSS)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteComJS)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteOtim)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteCDNpu)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteCDNpr)/nFrontEndPoucoExperientes100)
		barplot(aFrontEndPoucoExperienteProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Front-end Pouco Experientes")

		#### Experientes
		aFrontEndProcessosExperiente = c(nrow(ssFrontEndExperienteMinHTML)/nFrontEndExperientes100, nrow(ssFrontEndExperienteMinCSS)/nFrontEndExperientes100, nrow(ssFrontEndExperienteMinJS)/nFrontEndExperientes100, nrow(ssFrontEndExperienteComCSS)/nFrontEndExperientes100, nrow(ssFrontEndExperienteComJS)/nFrontEndExperientes100, nrow(ssFrontEndExperienteOtim)/nFrontEndExperientes100, nrow(ssFrontEndExperienteCDNpu)/nFrontEndExperientes100, nrow(ssFrontEndExperienteCDNpr)/nFrontEndExperientes100)
		barplot(aFrontEndExperienteProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Front-end Experientes")

		#### Experts
		aFrontEndProcessosExpert = c(nrow(ssFrontEndExpertMinHTML)/nFrontEndExperts100, nrow(ssFrontEndExpertMinCSS)/nFrontEndExperts100, nrow(ssFrontEndExpertMinJS)/nFrontEndExperts100, nrow(ssFrontEndExpertComCSS)/nFrontEndExperts100, nrow(ssFrontEndExpertComJS)/nFrontEndExperts100, nrow(ssFrontEndExpertOtim)/nFrontEndExperts100, nrow(ssFrontEndExpertCDNpu)/nFrontEndExperts100, nrow(ssFrontEndExpertCDNpr)/nFrontEndExperts100)
		barplot(aFrontEndExpertProcessos, ylim=c(0,100), xlim=c(0,11), ylab="%", space=0.1, density=5, angle=0, cex.names=0.7, names.arg=cProcessos, main="Processos\nDesenvolvedores Front-end Pouco Experts")

	### Comparação Front-end x Back-end
	barplot(matrix(c(aBackEndProcessos, aFrontEndProcessos), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cProcessos, main="Comparação dos Processos", legend.text=c("Back-end", "Front-end"))

	#### Dividido por Experiência

		#### Inexperientes
		barplot(matrix(c(aBackEndProcessosInexperiente, aFrontEndProcessosInexperiente), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cProcessos, main="Comparação dos Processos\nentre Inexperientes", legend.text=c("Back-end", "Front-end"))

		#### Pouco Experientes
		barplot(matrix(c(aBackEndProcessosPoucoExperiente, aFrontEndProcessosPoucoExperiente), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cProcessos, main="Comparação dos Processos\nentre Pouco Experientes", legend.text=c("Back-end", "Front-end"))

		#### Experientes
		barplot(matrix(c(aBackEndProcessosExperiente, aFrontEndProcessosExperiente), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cProcessos, main="Comparação dos Processos\nentre Experientes", legend.text=c("Back-end", "Front-end"))

		#### Experts
		barplot(matrix(c(aBackEndProcessosExpert, aFrontEndProcessosExpert), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.7, beside=T, col=c("blue", "red"), names.arg=cProcessos, main="Comparação dos Processos\nentre Experts", legend.text=c("Back-end", "Front-end"))
			
## Editor de Texto

	### Desenvolvedores Back-end
	aBackEndEditor = c(nrow(ssBackEndEditSub)/nBackEnd100, nrow(ssBackEndEditWeb)/nBackEnd100, nrow(ssBackEndEditNot)/nBackEnd100, nrow(ssBackEndEditVst)/nBackEnd100, nrow(ssBackEndEditDrw)/nBackEnd100, nrow(ssBackEndEditVim)/nBackEnd100, nrow(ssBackEndEditEma)/nBackEnd100, nrow(ssBackEndEditTxm)/nBackEnd100, nrow(ssBackEndEditNet)/nBackEnd100, nrow(ssBackEndEditEcl)/nBackEnd100, nrow(ssBackEndEditBra)/nBackEnd100, nrow(ssBackEndEditOth)/nBackEnd100)
	barplot(aBackEndEditor, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Back-end")

	#### Dividido por Experiência

		#### Inexperientes
		aBackEndEditorInexperiente = c(nrow(ssBackEndInexperienteEditSub)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditWeb)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditNot)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditVst)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditDrw)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditVim)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditEma)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditTxm)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditNet)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditEcl)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditBra)/nBackEndInexperientes100, nrow(ssBackEndInexperienteEditOth)/nBackEndInexperientes100)
		barplot(aBackEndEditorInexperiente, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Back-end Inexperientes")

		#### Pouco Experientes
		aBackEndEditorPoucoExperiente = c(nrow(ssBackEndPoucoExperienteEditSub)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditWeb)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditNot)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditVst)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditDrw)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditVim)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditEma)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditTxm)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditNet)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditEcl)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditBra)/nBackEndPoucoExperientes100, nrow(ssBackEndPoucoExperienteEditOth)/nBackEndPoucoExperientes100)
		barplot(aBackEndEditorPoucoExperiente, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Back-end Pouco Experientes")

		#### Experientes
		aBackEndEditorExperiente = c(nrow(ssBackEndExperienteEditSub)/nBackEndExperientes100, nrow(ssBackEndExperienteEditWeb)/nBackEndExperientes100, nrow(ssBackEndExperienteEditNot)/nBackEndExperientes100, nrow(ssBackEndExperienteEditVst)/nBackEndExperientes100, nrow(ssBackEndExperienteEditDrw)/nBackEndExperientes100, nrow(ssBackEndExperienteEditVim)/nBackEndExperientes100, nrow(ssBackEndExperienteEditEma)/nBackEndExperientes100, nrow(ssBackEndExperienteEditTxm)/nBackEndExperientes100, nrow(ssBackEndExperienteEditNet)/nBackEndExperientes100, nrow(ssBackEndExperienteEditEcl)/nBackEndExperientes100, nrow(ssBackEndExperienteEditBra)/nBackEndExperientes100, nrow(ssBackEndExperienteEditOth)/nBackEndExperientes100)
		barplot(aBackEndEditorExperiente, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Back-end Experientes")

		#### Experts
		aBackEndEditorExperts = c(nrow(ssBackEndExpertEditSub)/nBackEndExperts100, nrow(ssBackEndExpertEditWeb)/nBackEndExperts100, nrow(ssBackEndExpertEditNot)/nBackEndExperts100, nrow(ssBackEndExpertEditVst)/nBackEndExperts100, nrow(ssBackEndExpertEditDrw)/nBackEndExperts100, nrow(ssBackEndExpertEditVim)/nBackEndExperts100, nrow(ssBackEndExpertEditEma)/nBackEndExperts100, nrow(ssBackEndExpertEditTxm)/nBackEndExperts100, nrow(ssBackEndExpertEditNet)/nBackEndExperts100, nrow(ssBackEndExpertEditEcl)/nBackEndExperts100, nrow(ssBackEndExpertEditBra)/nBackEndExperts100, nrow(ssBackEndExpertEditOth)/nBackEndExperts100)
		barplot(aBackEndEditorExperts, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Back-end Experts")

	### Desenvolvedores Front-end
	aFrontEndEditor = c(nrow(ssFrontEndEditSub)/nFrontEnd100, nrow(ssFrontEndEditWeb)/nFrontEnd100, nrow(ssFrontEndEditNot)/nFrontEnd100, nrow(ssFrontEndEditVst)/nFrontEnd100, nrow(ssFrontEndEditDrw)/nFrontEnd100, nrow(ssFrontEndEditVim)/nFrontEnd100, nrow(ssFrontEndEditEma)/nFrontEnd100, nrow(ssFrontEndEditTxm)/nFrontEnd100, nrow(ssFrontEndEditNet)/nFrontEnd100, nrow(ssFrontEndEditEcl)/nFrontEnd100, nrow(ssFrontEndEditBra)/nFrontEnd100, nrow(ssFrontEndEditOth)/nFrontEnd100)
	barplot(aFrontEndEditor, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Front-end")

	#### Dividido por Experiência

		#### Inexperientes
		aFrontEndEditorInexperiente = c(nrow(ssFrontEndInexperienteEditSub)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditWeb)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditNot)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditVst)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditDrw)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditVim)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditEma)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditTxm)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditNet)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditEcl)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditBra)/nFrontEndInexperientes100, nrow(ssFrontEndInexperienteEditOth)/nFrontEndInexperientes100)
		barplot(aFrontEndEditorInexperiente, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Front-end Inexperientes")

		#### Pouco Experientes
		aFrontEndEditorPoucoExperiente = c(nrow(ssFrontEndPoucoExperienteEditSub)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditWeb)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditNot)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditVst)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditDrw)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditVim)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditEma)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditTxm)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditNet)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditEcl)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditBra)/nFrontEndPoucoExperientes100, nrow(ssFrontEndPoucoExperienteEditOth)/nFrontEndPoucoExperientes100)
		barplot(aFrontEndEditorPoucoExperiente, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Front-end Pouco Experientes")

		#### Experientes
		aFrontEndEditorExperiente = c(nrow(ssFrontEndExperienteEditSub)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditWeb)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditNot)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditVst)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditDrw)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditVim)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditEma)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditTxm)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditNet)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditEcl)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditBra)/nFrontEndExperientes100, nrow(ssFrontEndExperienteEditOth)/nFrontEndExperientes100)
		barplot(aFrontEndEditorExperiente, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Front-end Experientes")

		#### Experts
		aFrontEndEditorExperts = c(nrow(ssFrontEndExpertEditSub)/nFrontEndExperts100, nrow(ssFrontEndExpertEditWeb)/nFrontEndExperts100, nrow(ssFrontEndExpertEditNot)/nFrontEndExperts100, nrow(ssFrontEndExpertEditVst)/nFrontEndExperts100, nrow(ssFrontEndExpertEditDrw)/nFrontEndExperts100, nrow(ssFrontEndExpertEditVim)/nFrontEndExperts100, nrow(ssFrontEndExpertEditEma)/nFrontEndExperts100, nrow(ssFrontEndExpertEditTxm)/nFrontEndExperts100, nrow(ssFrontEndExpertEditNet)/nFrontEndExperts100, nrow(ssFrontEndExpertEditEcl)/nFrontEndExperts100, nrow(ssFrontEndExpertEditBra)/nFrontEndExperts100, nrow(ssFrontEndExpertEditOth)/nFrontEndExperts100)
		barplot(aFrontEndEditorExperts, ylim=c(0,100), xlim=c(0,13), ylab="%", space=0.16, density=5, angle=0, cex.names=0.65, names.arg=cEditores, main="Editores\nDesenvolvedores Front-end Experts")

	### Comparação Front-end x Back-end
	barplot(matrix(c(aBackEndEditor, aFrontEndEditor), 2, byrow=T), ylim=c(0,100), xlim=c(0,25), ylab="%", space=c(0,0.28), density=5, angle=0, cex.names=0.65, beside=T, col=c("blue", "red"), names.arg=cEditores, main="Comparação de Editores", legend.text=c("Back-end", "Front-end"))

	#### Dividido por Experiência

		#### Inexperientes
		barplot(matrix(c(aBackEndEditorInexperiente, aFrontEndEditorInexperiente), 2, byrow=T), ylim=c(0,100), xlim=c(0,25), ylab="%", space=c(0,0.28), density=5, angle=0, cex.names=0.65, beside=T, col=c("blue", "red"), names.arg=cEditores, main="Comparação de Editores\nentre Inexperientes", legend.text=c("Back-end", "Front-end"))

		#### Pouco Experientes
		barplot(matrix(c(aBackEndEditorPoucoExperiente, aFrontEndEditorPoucoExperiente), 2, byrow=T), ylim=c(0,100), xlim=c(0,25), ylab="%", space=c(0,0.28), density=5, angle=0, cex.names=0.65, beside=T, col=c("blue", "red"), names.arg=cEditores, main="Comparação de Editores\nentre Pouco Experientes", legend.text=c("Back-end", "Front-end"))

		#### Experientes
		barplot(matrix(c(aBackEndEditorExperiente, aFrontEndEditorExperiente), 2, byrow=T), ylim=c(0,100), xlim=c(0,25), ylab="%", space=c(0,0.28), density=5, angle=0, cex.names=0.65, beside=T, col=c("blue", "red"), names.arg=cEditores, main="Comparação de Editores\nentre Experientes", legend.text=c("Back-end", "Front-end"))

		#### Experts
		barplot(matrix(c(aBackEndEditorExperts, aFrontEndEditorExperts), 2, byrow=T), ylim=c(0,100), xlim=c(0,25), ylab="%", space=c(0,0.28), density=5, angle=0, cex.names=0.65, beside=T, col=c("blue", "red"), names.arg=cEditores, main="Comparação de Editores\nentre Experts", legend.text=c("Back-end", "Front-end"))	

# Exemplo de como salvar
# png(filename="graficos/Novas_Ferramentas_Praticas_Comparacao_4_Experts.png", width=1146, height=528, pointsize=16)
# barplot(matrix(c(aBackEndPraticasExperts, aFrontEndPraticasExperts), 2, byrow=T), ylim=c(0,100), xlim=c(0,20), ylab="%", space=c(0,0.1), density=5, angle=0, cex.names=0.65, beside=T, col=c("blue", "red"), names.arg=cFerramPraticas, main="Comparação\ndo Uso de Novas Ferramentas e Práticas\nentre Experts", legend.text=c("Back-end", "Front-end")
# dev.off()


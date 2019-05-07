import time
import selenium
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as ec
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import unittest

#wait = None
#driver = None

from dicionario import x

def menu_click(wait, texto_visivel):

    elemento = wait.until(ec.element_to_be_clickable( (By.XPATH, "//md-menu/div/button/div[text()='"+texto_visivel+"']") ))
    elemento.click()
    return elemento


def wait_side_nav():
    time.sleep(1)
    wait.until(ec.invisibility_of_element( (By.CSS_SELECTOR,".md-sidenav-backdrop.md-opaque.ng-scope.ng-animate.ng-leave.ng-leave-active") ))
    wait.until(ec.invisibility_of_element((By.ID, "loading-bar")))

def wait_loading():
    try:
        wait.until(ec.visibility_of_element_located((By.ID, "loading-bar")))
    except selenium.common.exceptions.TimeoutException:
        pass
    wait.until(ec.invisibility_of_element((By.ID, "loading-bar")))
    wait.until(ec.invisibility_of_element((By.CSS_SELECTOR, ".md-sidenav-backdrop.md-opaque.ng-scope.ng-animate.ng-leave.ng-leave-active")))


def logar():

    usuario = "xxx" #inserir cpf do perfil inclusor
    senha = "xxx" #inserir senha do perfil inclusor
    #url_acessos = "http://acessosmp.intra.planejamento.gov.br/"
    url_acessos = "http://acessosmp.planejamento.gov.br/"
    driver.get(url_acessos)
    driver.find_element_by_css_selector(".md-icon-button.launch.md-button.ng-scope.md-ink-ripple").click()
    driver.find_element_by_css_selector("#username").send_keys(usuario)
    driver.find_element_by_css_selector("#password").send_keys(senha)
    driver.find_element_by_css_selector("#loginform button").click()
    #clicar aba
    wait_loading()
    driver.find_element_by_css_selector(".menu.md-button.md-ink-ripple").click()
    menu_click(wait, "Usuario ")
    wait.until(ec.element_to_be_clickable( (By.LINK_TEXT, "Consultar Usuario") )).click()
    wait_side_nav();
def preencher_usuario(colaborador):
    voltar = wait.until(ec.visibility_of_element_located((By.XPATH, '//*[@id="conteudo"]/div/div/div/div/form/div/md-input-container/input'))).send_keys(colaborador)
    wait_side_nav();
    wait.until(ec.element_to_be_clickable((By.ID, "consultarUsuario_Button"))).click()
    wait_loading()
    wait.until(ec.element_to_be_clickable((By.ID, "concederAcesso_Button"))).click()
    wait_loading()
def inserir_perfil(UG, perfil, processo):
    wait.until(ec.element_to_be_clickable((By.ID, "concederAcesso_Button")))
    wait_loading()
    wait.until(ec.visibility_of_element_located((By.XPATH,'//*[@id="conteudo"]/div/div/div/md-content/form/section/div/div[5]/button[2]/span[text()="Limpar"]'))).click()
    wait_loading()
    driver.execute_("arguments[0].scrollIntoView(true);", wait.until(ec.element_to_be_clickable((By.ID, "concederAcesso_Button"))))
    wait_side_nav() #mudança
    wait.until(ec.element_to_be_clickable((By.CSS_SELECTOR, "[name='sistema']"))).click()
    wait_side_nav()
    wait.until(ec.visibility_of_element_located((By.XPATH, '//md-select-menu/md-content/md-option/div[text()="Sistema Unificado"]'))).click()
    wait_side_nav() #mudança
    wait.until(ec.element_to_be_clickable((By.NAME, "modulo"))).click()
    wait_side_nav() #mudançaaaaaa
    wait.until(ec.visibility_of_element_located((By.XPATH, '//md-select-menu/md-content/md-option/div[text()="Serviços"]'))).click()
    wait_side_nav()
    # wait.until(ec.visibility_of_element_located((By.XPATH, '//div/div/div/md-content/form/section/div/div[2]/md-input-container/md-autocomplete/md-autocomplete-wrap/button'))).click()
    #time.sleep(1)
    wait.until(ec.visibility_of_element_located((By.XPATH,"//label[text()='UG Executora:']/following-sibling::md-autocomplete/md-autocomplete-wrap/input"))).send_keys(UG)
    wait_side_nav() #mudança
    wait.until(ec.visibility_of_element_located((By.XPATH,"//label[text()='UG Executora:']/following-sibling::md-autocomplete/md-autocomplete-wrap/input"))).send_keys(Keys.ARROW_UP, Keys.ENTER)
    # wait_loading()
    wait.until(ec.invisibility_of_element((By.CSS_SELECTOR, ".md-scroll-mask")))
    # wait.until(ec.visibility_of_element_located((By.CSS_SELECTOR, ".ng-scope.md-input.ng-valid-minlength.ng-valid-maxlength.ng-valid.ng-valid-required.ng-dirty.ng-touched"))).send_keys(Keys.ARROW_UP, Keys.ENTER)
    wait.until(ec.element_to_be_clickable((By.CSS_SELECTOR, "[name='perfil']"))).click()
    perfil_input = wait.until(ec.element_to_be_clickable((By.XPATH, "//md-select-menu/md-content/md-option/div[text()='" + perfil + "']")))
    driver.execute_("arguments[0].scrollIntoView(true);", perfil_input)
    perfil_input.click()
    wait_side_nav()
    just = wait.until(ec.element_to_be_clickable((By.NAME, "justificativa")))
    wait_side_nav() #mudança
    just.send_keys(processo)
    time.sleep(1)
    wait.until(ec.element_to_be_clickable((By.ID, "concederAcesso_Button"))).click()
    time.sleep(4)






colaboradores = ["14499940672"]


driver = webdriver.Chrome("C:/chromedriver.exe")
wait = WebDriverWait(driver, 5)

#colaborador = "xxx" #inserir cpf do colaborador
processo = "04982.000207/2019-47" #inserir numero do processo
UG = "SUPERINTENDENCIA DO PATRIMONIO DA UNIAO/AL" #inserir nome da UG
perfis=[17,18] #inserir perfils

# 1,2,3
logar()
print("\nPERFIS SOLICITADOS: \n")

###



for i in range(len(perfis)):
    print(x[perfis[i]])
    #print("\n")

i=0
print("\nADICIONANDO...\n")


for c in colaboradores:
    print("\nINICIANDO INSERÇÃO DO CPF: ", c)
    preencher_usuario(c)
    for p in perfis:
        k=x[p]
        print(k)
        inserir_perfil(UG, k , processo)

    print(("INCLUSÃO DOS PERFIS DO USUÁRIO CONCLUIDA!\n\n"))

    wait.until(ec.element_to_be_clickable((By.ID, "voltar_Button"))).click()
    voltar = wait.until(ec.visibility_of_element_located((By.XPATH,'//*[@id="conteudo"]/div/div/div/div/form/div/md-input-container/input'))).clear()
    #voltar.click()

import java.util.Scanner;

public class asgment {
    static double haraaga = 150;
    static int pin = 3188;
    static String[] taariikh = new String[50];
    static int tIndex = 0;
    public static final int BANK_PIN_NUMBER = 2555;
    static double bankBalance = 500.0;

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Fadlan geli: ");
        String code = input.nextLine();

        if (!code.equals("*770#")) {
            System.out.println("Nambarka aad gelisay waa khalad!");
            return;
        }

        if (!tijaabiPin(input)) return;

        int doorasho;
        do {
            muujiMenu();
            doorasho = input.nextInt();
            qabsoDoorasho(doorasho, input);
        } while (doorasho != 0);

        System.out.println("Mahadsanid isticmaalka EVCPlus App.");
        input.close();
    }

    public static boolean tijaabiPin(Scanner input) {
        int iskuDayo = 0;

        while (iskuDayo < 3) {
            System.out.print("Fadlan geli PIN-kaaga: ");
            int userPin = input.nextInt();
            if (userPin == pin) {
                return true;
            } else {
                System.out.println("PIN waa khalad. Isku day mar kale.");
                iskuDayo++;
            }
        }
        System.out.println("Waxaad dhaaftay tiradii la oggolaa.");
        return false;
    }

    public static void muujiMenu() {
        System.out.println("\n---  Adeegyada EVCPlus ---");
        System.out.println("1. Itus Haraaga");
        System.out.println("2. karkahadalka");
        System.out.println("3. Bixi Biil");
        System.out.println("4. Uwareeji EVC");
        System.out.println("5. Warbixin Kooban");
        System.out.println("6. Salaam Bank");
        System.out.println("7. Bedel PIN");
        System.out.println("8. Kordhi Xisaabta");
        System.out.println("0. Bixi");
        System.out.print("Dooro adeeg: ");
    }

    public static void qabsoDoorasho(int doorasho, Scanner input) {
        switch (doorasho) {
            case 1:
                tusHaraaga();
                break;
            case 2:
                kaarkaHadalka(input);
                break;
            case 3:
                bixiBiil(input);
                break;
            case 4:
                uwareejiEVC(input);
                break;
            case 5:
                tusTaariikh();
                break;
            case 6:
                handleBank(input);
                break;
            case 7:
                maareynta(input);
                break;
            case 8:
                kordhiXisaab(input);
                break;
            case 0:
                System.out.println("Waad baxday.");
                break;
            default:
                System.out.println("Fadlan dooro number sax ah.");
        }
    }

    public static void tusHaraaga() {
        System.out.printf("Haraagaagu waa: $%.2f\n", haraaga);
        kuDarTaariikh("Haraag la fiiriyay");
    }




    public static void kaarkaHadalka(Scanner input) {
        while (true) {
            System.out.println("\n=== Kaarka hadalka ===");
            System.out.println("1. Ku Shubo Airtime");
            System.out.println("2. Ugu Shub Airtime");
            System.out.println("3. MIFI Packages");
            System.out.println("4. Ku shubo Internet");
            System.out.println("5. Ugu shub qof kale (MMT)");
            System.out.println("0. Back");

            System.out.print("Dooro ikhtiyaar: ");
            int choice = input.nextInt();
            input.nextLine(); // clean newline

            switch (choice) {
                case 1 -> {
                    System.out.println("\n== Ku Shubo Airtime ==");
                    System.out.print("Geli qadarka: ");
                    double amount = input.nextDouble();
                    input.nextLine();
                    System.out.println("Waxaad ku shubatay " + amount + " units.");
                }
                case 2 -> {
                    System.out.println("\n== Ugu Shub Airtime ==");
                    System.out.print("Geli lambarka qofka: ");
                    String number = input.nextLine();
                    System.out.print("Geli qadarka: ");
                    double amount = input.nextDouble();
                    input.nextLine();
                    System.out.println("Waxaad ugu shubtay " + amount + " qofka " + number);
                }
                case 3 -> {
                    System.out.println("\n== MIFI Packages ==");
                    System.out.println("1. 5GB - 5 maalmood");
                    System.out.println("2. 10GB - 10 maalmood");
                    System.out.println("3. 20GB - 30 maalmood");
                    System.out.print("Dooro xirmo: ");
                    int x = input.nextInt();
                    input.nextLine();
                    switch (x) {
                        case 1 -> System.out.println("5GB xirmo ayaa laguu shubay.");
                        case 2 -> System.out.println("10GB xirmo ayaa laguu shubay.");
                        case 3 -> System.out.println(" 20GB xirmo ayaa laguu shubay.");
                        default -> System.out.println("Doorasho aan sax aheyn.");
                    }
                }
                case 4 -> {
                    System.out.println("\n== Ku Shubo Internet ==");
                    System.out.print("Geli qadarka MB: ");
                    int mb = input.nextInt();
                    input.nextLine();
                    System.out.println("" + mb + "MB ayaa laguu shubay.");
                }
                case 5 -> {
                    System.out.println("\n== Ugu shub qof kale (MMT) ==");
                    System.out.print("Geli lambarka qofka: ");
                    String num = input.nextLine();
                    System.out.print("Geli qadarka: ");
                    double am = input.nextDouble();
                    input.nextLine();
                    System.out.println( " ayaa loo shubay qofka " + num + " adigoo adeegsanaya MMT.");
                }
                case 0 -> {
                    System.out.println("Waxaa lagaa saaray Kaarka Hadalka menu.");
                    return;
                }
                default -> System.out.println("Fadlan dooro ikhtiyaar sax ah.");
            }
        }
    }

    public static void bixiBiil(Scanner input) {
        System.out.println("1. Biyaha\n2. Koronto\n3. Internet");
        System.out.print("Dooro adeeg: ");
        int biilNooca = input.nextInt();

        String biilMagac = "";
        if (biilNooca == 1) biilMagac = "Biyaha";
        else if (biilNooca == 2) biilMagac = "Koronto";
        else if (biilNooca == 3) biilMagac = "Internet";
        else {
            System.out.println("Doorasho khaldan.");
            return;
        }

        System.out.print("Geli lacagta biilka: ");
        double lacag = input.nextDouble();
        if (lacag <= 0) {
            System.out.println("Lacag khaldan.");
            return;
        }
        if (lacag <= haraaga) {
            haraaga -= lacag;
            System.out.println("Biilka " + biilMagac + " waa la bixiyay.");
            kuDarTaariikh("Biil bixis: " + biilMagac + " $" + lacag);
        } else {
            System.out.println("Haraaga kuma filna.");
        }
    }

    public static void uwareejiEVC(Scanner input) {
        System.out.print("Geli numberka: ");
        String qaataha = input.next();
        System.out.print("Geli lacagta: ");
        double lacag = input.nextDouble();

        if (lacag <= 0) {
            System.out.println("Lacag khaldan.");
            return;
        }

        if (lacag <= haraaga) {
            haraaga -= lacag;
            System.out.println("Waad u wareejisay $" + lacag + " -> " + qaataha);
            kuDarTaariikh("Wareejin: $" + lacag + " -> " + qaataha);
        } else {
            System.out.println("Haraaga kuma filna.");
        }
    }

    public static void tusTaariikh() {
        System.out.println("--- Warbixin ---");
        for (int i = 0; i < taariikh.length; i++) {
            if (taariikh[i] != null) {
                System.out.println((i + 1) + ". " + taariikh[i]);
            }
        }
    }

    public static void handleBank(Scanner input) {
        System.out.print("Geli PIN-ka Bangiga: ");
        int enteredPin = input.nextInt();

        if (enteredPin == BANK_PIN_NUMBER) {
            String[] options = {
                    "1. Itus Haraagaaga",
                    "2. Lacag Dhigasho",
                    "3. Lacag Qaado",
                    "4. Ka wareeji EVCP-lus",
                    "5. Ka wareeji Account-kaga",
                    "6. Hubi Wareejinta Account-ka",
                    "7. Ka bax"
            };

            boolean bankRunning = true;
            while (bankRunning) {
                System.out.println("\n------ Salaam Bank ------");
                for (String opt : options) {
                    System.out.println(opt);
                }

                System.out.print("Dooro: ");
                int bankChoice = input.nextInt();

                switch (bankChoice) {
                    case 1:
                        System.out.printf("Haraaga Bangiga: $%.2f\n", bankBalance);
                        break;
                    case 2:
                        System.out.print("Geli lacagta aad dhigaysid: ");
                        double deposit = input.nextDouble();
                        bankBalance += deposit;
                        System.out.println("Waad dhigatay $" + deposit);
                        break;
                    case 3:
                        System.out.print("Geli lacagta aad qaadanaysid: ");
                        double withdraw = input.nextDouble();
                        if (bankBalance >= withdraw) {
                            bankBalance -= withdraw;
                            System.out.println("Waad qaadatay $" + withdraw);
                        } else {
                            System.out.println("Haraag kugu filan ma jiro!");
                        }
                        break;
                    case 4:
                        transferFromEVCPToBank(input);
                        break;
                    case 5:
                        transferFromBankToEVCP(input);
                        break;
                    case 6:
                        System.out.println("Hubinta wareejinta... (tani waa feature been ah)");
                        break;
                    case 7:
                        System.out.println("Waad ka baxday Salaam Bank");
                        bankRunning = false;
                        break;
                    default:
                        System.out.println("Doorasho khaldan!");
                }
            }
        } else {
            System.out.println("PIN khaldan!");
        }
    }

    public static void transferFromEVCPToBank(Scanner input) {
        System.out.print("Geli lacagta aad wareejinayso: ");
        double amount = input.nextDouble();
        if (amount <= haraaga) {
            haraaga -= amount;
            bankBalance += amount;
            System.out.println("Waad wareejisay $" + amount + " EVCP -> Bank");
        } else {
            System.out.println("Haraaga EVCP kuma filna.");
        }
    }

    public static void transferFromBankToEVCP(Scanner input) {
        System.out.print("Geli lacagta aad wareejinayso: ");
        double amount = input.nextDouble();
        if (amount <= bankBalance) {
            bankBalance -= amount;
            haraaga += amount;
            System.out.println("Waad wareejisay $" + amount + " Bank -> EVCP");
        } else {
            System.out.println("Bank-ga kuma filna lacagtaas.");
        }
    }

    // Method-ka weyn ee Maareynta
    public static void maareynta(Scanner akhri) {
        int doorasho;
        do {
            System.out.println("Maareynta");
            System.out.println("1. Bedel lambarka sirta ah");
            System.out.println("2. Bedel luqadda");
            System.out.println("3. Wargelin Mobile lumay");
            System.out.println("4. Xiro lacag");
            System.out.println("5. Soo celi lacag khaldan");
            System.out.println("0. Ka noqo");

            System.out.print("Fadlan dooro mid: ");
            doorasho = akhri.nextInt();

            switch (doorasho) {
                case 1:
                    bedelLambarSir(akhri);
                    break;
                case 2:
                    bedelLuqad(akhri);
                    break;
                case 3:
                    mobileLumay();
                    break;
                case 4:
                    xiroLacag(akhri);
                    break;
                case 5:
                    celiLacagKhaldan(akhri);
                    break;
                case 0:
                    System.out.println("Waxaad ku noqotay menu-ga hore.");
                    break;
                default:
                    System.out.println("Fadlan dooro tiro sax ah.");
            }
        } while (doorasho != 0);
    }

    public static void bedelLambarSir(Scanner akhri) {
        System.out.print("Geli lambarka sirta cusub: ");
        String lambarCusub = akhri.next();
        System.out.println("Lambarka sirta waa la bedelay : " + lambarCusub);
    }

    public static void bedelLuqad(Scanner akhri) {
        System.out.println("Dooro luqadda:");
        System.out.println("1. Soomaali");
        System.out.println("2. English");
        int luqad = akhri.nextInt();
        if (luqad == 1) {
            System.out.println("Luqaddaada hadda waa Soomaali.");
        } else if (luqad == 2) {
            System.out.println("Your language is now English.");
        } else {
            System.out.println("Doorasho aan sax ahayn.");
        }
    }

    public static void mobileLumay() {
        System.out.println("Wargelin: Mobile-ka lumay waa la xiray. Fadlan la xiriir adeegga macaamiisha.");
    }

    public static void xiroLacag(Scanner akhri) {
        System.out.print("Geli lacagta aad rabto inaad xayirto: ");
        double lacag = akhri.nextDouble();
        System.out.println("Waxaad xayitay lacag dhan $" + lacag);
    }

    public static void celiLacagKhaldan(Scanner akhri) {
        System.out.print("Geli lambarka aad lacagta khaldan ugu dirtay: ");
        String lambarKhaldan = akhri.next();
        System.out.print("Geli lacagta luntay: ");
        double luntay = akhri.nextDouble();
        System.out.println("Codsiga soo celinta $" + luntay + " ee " + luntay + " waa la diiwaangeliyey.");
    }

    public static void kordhiXisaab(Scanner input) {
        System.out.print("Geli lacagta aad rabto inaad ku kordhiso: ");
        double lacag = input.nextDouble();
        if (lacag <= 0) {
            System.out.println("Lacag khaldan.");
            return;
        }
        haraaga += lacag;
        System.out.println("Haraaga cusub: $" + haraaga);
        kuDarTaariikh("Kordhis: $" + lacag);
    }

    public static void kuDarTaariikh(String ficil) {
        if (tIndex < taariikh.length) {
            taariikh[tIndex] = ficil;
            tIndex++;
        } else {
            tIndex = 0;
            taariikh[tIndex] = ficil;
            tIndex++;
        }
    }
}

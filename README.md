# firstproject
 import java.util.ArrayList;
import java.util.Scanner;

//SERIES MODEL NAMES
class SeriesModel
{
    public String SeriesId;
    public String SeriesName;
    public String SeriesAge;
    public String SeriesNumberOfEpisodes;
}
public class Movies {
    static ArrayList<SeriesModel> seriesList = new ArrayList<>();
    static Scanner input = new Scanner(System.in);

    //THE MAIN METHOD
    public static void main(String[] args) {
        System.out.println("LATEST SERIES - 2025");
        System.out.println("*********************************");
        System.out.println("Enter (1) to launch menu or any other key to exit: ");
        String start = input.nextLine();

        if (!start.equals("1")) {
            System.out.println("Exiting.");
            return;
        }
        menu();
    }

    //THE MENU METHOD
    public static void menu() {
        while (true) {
            System.out.println("\nPlease select one of the following menu items:");
            System.out.println("(1) Capture a new series.");
            System.out.println("(2) Search for a series.");
            System.out.println("(3) Update series.");
            System.out.println("(4) Delete a series.");
            System.out.println("(5) Print series report – 2025");
            System.out.println("(6) Exit Application.");
            System.out.print("Choice: ");
            String choice = input.nextLine();

            switch (choice) {
                case "1":
                    CaptureSeries();
                    break;
                case "2":
                    SearchSeries();
                    break;
                case "3":
                    UpdateSeries();
                    break;
                case "4":
                    DeleteSeries();
                    break;
                case "5":
                    SeriesReport();
                    break;
                case "6":
                    System.out.println("Exiting application...");
                    return;
                default:
                    System.out.println("Invalid option");
            }
        }
    }

    //METHOD WERE YOU CAN CAPTURE A NEW SERIES
    public static void CaptureSeries() {
        System.out.println("\nCapture A New Series");
        System.out.println("********************************");
        SeriesModel model = new SeriesModel();

        System.out.println("Enter the series id>> ");
        model.SeriesId = input.nextLine();
        System.out.println("Enter the series name>> ");
        model.SeriesName = input.nextLine();
        model.SeriesAge = getValidAge();
        System.out.println("Enter the number of episodes for " + model.SeriesName + ":");
        model.SeriesNumberOfEpisodes = input.nextLine();
        seriesList.add(model);
        System.out.println("Series processed successfully!!");
    }

    //METHOD WERE YOU CAN ENTER THE AGE RESTRICTIONS
    public static String getValidAge() {
        while (true) {
            System.out.print("Enter the series age restriction: ");
            String ageInput = input.nextLine();
            try {
                int age = Integer.parseInt(ageInput);
                if (age >= 2 && age <= 18) {
                    return String.valueOf(age);
                } else {
                    System.out.println("You have entered an incorrect series age!!!");
                    System.out.println("Please re-enter the series age >> ");
                }
            } catch (NumberFormatException e) {
                System.out.println("You have entered an incorrect series age!!!");
                System.out.println("Please re-enter the series age >> ");
            }
        }
    }

    //METHOD WERE TOU CAN SEARCH A SERIES
    public static void SearchSeries() {
        System.out.println("Enter the series id to search");
        String id = input.nextLine();
        for (SeriesModel model : seriesList) {
            if (model.SeriesId.equals(id)) {
                System.out.println("Series Found: ");
                System.out.println("ID: " + model.SeriesId);
                System.out.println("Name: " + model.SeriesName);
                System.out.println("Age Restrictions: " + model.SeriesAge);
                System.out.println("Number of Episodes: " + model.SeriesNumberOfEpisodes);
                return;
            }
        }
        System.out.println("Series Not Found");
    }

    //METHOD WERE YOU CAN DELETE A SERIES
    public static void DeleteSeries() {
        System.out.println("Enter the series id to Delete: ");
        String id = input.nextLine();
        for (SeriesModel model : seriesList) {
            if (model.SeriesId.equals(id)) {
                seriesList.remove(model);
                System.out.println("Series deleted successfully");
                return;
            }
        }
        System.out.println("Series not found");
    }

    //METHOD WERE YOU CAN GET A SERIES LIST
    public static void SeriesReport() {
        System.out.println("\nSERIES REPORT – 2025");
        System.out.println("*************************");
        for (SeriesModel model : seriesList) {
            System.out.println("ID: " + model.SeriesId + "| Name: " + model.SeriesName + "| Age restriction: " + model.SeriesAge + "| Episodes: " + model.SeriesNumberOfEpisodes);
        }
    }

    //METHOD WERE YOU CAN UPDATE A SERIES OF YOUR CHOICE
    public static void UpdateSeries() {
        System.out.println("Enter the series id to Update");
        String id = input.nextLine();
        for (SeriesModel model : seriesList) {
            if (model.SeriesId.equals(id)) {
                System.out.println("Series Found Enter new Details: ");

                System.out.println("Enter new series id: ");
                model.SeriesName = input.nextLine();
                System.out.println("Enter new series name: ");
                model.SeriesName = input.nextLine();
                model.SeriesAge = getValidAge();
                System.out.println("Enter new number of Episodes: ");
                model.SeriesNumberOfEpisodes = input.nextLine();

                System.out.println("Series details updated successfully! ");
                return;
            }
        }
        System.out.println("Series not Found!");
    }
}

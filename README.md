# THB1
package bt2b.newpackage;

import java.text.NumberFormat;
import java.text.SimpleDateFormat;
import java.util.Calendar;
import java.util.Date;
import java.util.Locale;

/**
 *
 * @author MSI-PC
 */
public class HangThucPham {
    private int maHang;
    private String tenHang;
    private double donGia;
    private Date nSX, hSD;

    public HangThucPham(int maHang, String tenHang, double donGia, Date nSX, Date hSD) {
        this.maHang = maHang;
        this.tenHang = tenHang;
        this.donGia = donGia;
        this.nSX = nSX;
        this.hSD = hSD;
    }
    public HangThucPham() {
    }
    public int getMaHang() {
        return maHang;
    }
 
    public void setMaHang(int maHang) {
        this.maHang = maHang;
    }
 
    public String getTenHang() {
        return tenHang;
    }
 
    public void setTenHang(String tenHang) {
        this.tenHang = tenHang;
    }
 
    public double getDonGia() {
        return donGia;
    }
 
    public void setDonGia(double donGia) {
        this.donGia = donGia;
    }
 
    public Date getnSX() {
        return nSX;
    }
 
    public void setnSX(Date nSX) {
        this.nSX = nSX;
    }
 
    public Date gethSD() {
        return hSD;
    }
 
    public void sethSD(Date hSD) {
        this.hSD = hSD;
    }
    public String toString() {
       
        Locale localeVN = new Locale("vi", "VN");
        NumberFormat numberFormat = NumberFormat.getCurrencyInstance(localeVN);
        String str = numberFormat.format(donGia);
       
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat("dd/MM/yyyy");
        String str1 = simpleDateFormat.format(nSX);
        String str2 = simpleDateFormat.format(hSD);
        return "Thong tin ve thuc pham: \n" +
                "Ma hang : " + maHang +
                "\nTen hang : '" + tenHang +
                "\nĐon gia : " + str +
                "\nNgay san xuat : " + str1 +
                "\nHan su dung : " + str2
                ;                   
    }
    public void setNSX(int year, int month, int day) {
        Calendar calendar = Calendar.getInstance();
        calendar.set(year, month - 1, day);
        this.nSX = calendar.getTime();
    }
    public void setHSD(int year, int month, int day) {
        Calendar calendar = Calendar.getInstance();
        calendar.set(year, month - 1, day);
        this.hSD = calendar.getTime();
    }
    public boolean kiemTraTenHang(boolean k) {
        if (this.tenHang == "" || this.tenHang.isEmpty()) {
            System.out.println("Ten hang khong đuoc đe trong : ");
        } else {
            k = false;
        }
        return k;
    }
    public boolean kiemTraNgay(boolean t) {
        if (this.getnSX().compareTo(this.gethSD()) < 0) {
            t = false;
        } else {
            System.out.println("Ngay het han khong đuoc nho hon ngay san xuat : ");
        }
        return t;
    }
    public void kiemTraHSD() {
        Date today = new Date();
        today.getTime();
SimpleDateFormat simpleDateFormat = new SimpleDateFormat("dd/MM/yyyy");
        String st = simpleDateFormat.format(today);
        if (this.gethSD().compareTo(today) < 0) {
            System.out.println("Hom nay la ngay " + st + ", hang hoa đa het han ");
        } else {
            System.out.println("Hom nay la ngay " + st + ", hang hoa van con ha n ");
        }
    }
}

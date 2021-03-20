getDataInListCtrl=function (listDivId) {
    var result = [];
    var listDiv = dom.byId(listDivId);
    var nColumnCount = 0;
    var divHead = listDiv.tHead.rows[0].children;
    var nColumnSize = divHead.length;
    var nRowIndex = 0;
    var divRow = null;
    var divText = '';
    for (; nRowIndex < nColumnSize; nRowIndex++) {
        divRow = null;
        divText = '';
        divRow = divHead[nRowIndex];
        divText = divRow.innerText;
        if (divText.length > 0) {
            if (!result[0]) {
                result[0] = new Array();
            }
            result[0][nRowIndex] = divText;
            nColumnCount++;
        }
    }

    var divBody = listDiv.tBodies[0].children;
    if (!divBody) {
        return;
    }
    var nRowCount = divBody.length;
    if (nRowCount <= 0) {
        return;
    }

    nRowIndex = 0;
    var nColumnIndex = 0;
    for (; nRowIndex < nRowCount; nRowIndex++) {
        divRow = divBody[nRowIndex];
        for (; nColumnIndex < nColumnCount; nColumnIndex++) {
            divText = divRow.cells[nColumnIndex].innerText;
            if (!result[nRowIndex + 1]) {
                result[nRowIndex + 1] = new Array();
            }
            result[nRowIndex + 1][nColumnIndex] = divText;
        }
    }
    return result;
}
